---
title: TN053:DAO 資料庫類別的自訂 DFX 常式
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dfx
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: b610604c1b7a68128dc9eb6fb5515225ed22b16e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399677"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053:DAO 資料庫類別的自訂 DFX 常式

> [!NOTE]
>  視覺效果C++環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您改用[OLE DB 樣板](../data/oledb/ole-db-templates.md)或是[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)針對新的專案。 您只應該使用 DAO，在維護現有的應用程式。

這個技術提示說明 DAO 資料錄欄位交換 (DFX) 機制。 若要協助您了解 DFX 常式中的情況`DFX_Text`函式將會說明在做為範例的詳細資料。 為這個技術提示資訊的其他來源，您可以檢查程式碼為其他個別的 DFX 函式。 您可能不需要自訂 DFX 常式視您可能需要自訂 RFX 常式 （使用 ODBC 資料庫類別使用）。

這個技術提示包含：

- DFX 概觀

- [範例](#_mfcnotes_tn053_examples)使用 DAO 資料錄欄位交換和動態繫結

- [DFX 的運作方式](#_mfcnotes_tn053_how_dfx_works)

- [您的自訂 DFX 常式的用途](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text 的詳細資料](#_mfcnotes_tn053_details_of_dfx_text)

**DFX 概觀**

DAO 資料錄欄位交換 (DFX) 機制用來簡化的擷取和更新資料時使用的程序`CDaoRecordset`類別。 此程序已簡化使用的資料成員`CDaoRecordset`類別。 藉由衍生自`CDaoRecordset`，您可以加入代表資料表或查詢中的每個欄位的衍生類別中的資料成員。 這項 「 靜態繫結 」 機制很簡單，但它可能無法針對所有應用程式選擇的資料擷取/更新方法。 DFX 會擷取每個繫結的欄位每次目前資料錄變更時。 如果您正在開發的重視效能的應用程式，不需要變更貨幣時，擷取每個欄位 「 動態繫結 」 透過`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`可能選擇的資料存取方法。

> [!NOTE]
>  DFX 和動態繫結不會互斥，所以可以使用靜態和動態繫結的混合式用法。

## <a name="_mfcnotes_tn053_examples"></a> 範例 1 — 的 DAO 資料錄欄位交換只會使用

(假設`CDaoRecordset`-衍生的類別`CMySet`尚未開啟)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**只有動態的繫結的範例 2： 使用**

(假設使用`CDaoRecordset`類別， `rs`，並已開啟)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**範例 3 — 使用的 DAO 資料錄欄位交換，並動態繫結**

(假設使用的瀏覽 employee 資料`CDaoRecordset`-衍生的類別`emp`)

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="_mfcnotes_tn053_how_dfx_works"></a> DFX 的運作方式

DFX 機制的運作方式類似於 MFC ODBC 類別所使用的資料錄欄位交換 (RFX) 機制。 DFX 和 RFX 的原則都相同，但有許多內部的差異。 DFX 函式的設計是，幾乎所有的程式碼由個別的 DFX 常式共用。 在最高等級 DFX 只執行幾件事。

- DFX 建構 SQL**選取 **子句和 SQL**參數**子句，如有必要。

- DFX 建構供 DAO 的繫結結構`GetRows`函式 （稍後詳述）。

- DFX 管理用來偵測已變更的欄位 （如果正在使用雙重緩衝） 的資料緩衝區

- 管理 DFX **NULL**並**DIRTY**狀態陣列，並更新如有必要設定的值。

機制是核心的 DFX`CDaoRecordset`衍生類別的`DoFieldExchange`函式。 此函式將呼叫分派至適當的作業類型的個別的 DFX 函式。 然後再呼叫`DoFieldExchange`內部的 MFC 函式會將作業類型。 下列清單顯示的各種作業類型和簡短描述。

|運算|描述|
|---------------|-----------------|
|`AddToParameterList`|組建參數子句|
|`AddToSelectList`|組建的 SELECT 子句|
|`BindField`|設定繫結結構|
|`BindParam`|設定參數值|
|`Fixup`|設定 NULL 狀態|
|`AllocCache`|配置已變更的核取的快取|
|`StoreField`|將目前的記錄儲存至快取|
|`LoadField`|成員值的還原快取|
|`FreeCache`|釋放快取|
|`SetFieldNull`|設定欄位狀態 & 為 NULL 的值|
|`MarkForAddNew`|標記已變更的欄位如果不是虛擬 NULL|
|`MarkForEdit`|標記的欄位已變更如果不符合快取|
|`SetDirtyField`|將欄位標示為中途的值|

在下一步 區段中，每個作業將會說明詳細的`DFX_Text`。

若要了解有關 DAO 資料錄欄位交換程序最重要的功能是它會使用`GetRows`函式的`CDaoRecordset`物件。 DAO`GetRows`函式可在數種方式運作。 這個技術提示將只會簡短說明`GetRows`超出範圍的這個技術提示所顯示的原狀。

DAO`GetRows`能以數種方式。

- 它可以擷取多個記錄和多個欄位的資料一次。 這允許更快速的資料存取與複雜的處理大型資料結構和每個欄位的適當位移的資料結構中的每一筆記錄。 MFC 不會利用這個擷取機制的多個記錄。

- 另一種方式`GetRows`可以工作可讓程式設計人員指定每個欄位的一筆記錄的資料擷取的資料繫結位址。

- DAO 會也 「 回呼 」 呼叫端的可變長度資料行才能允許呼叫端配置的記憶體。 此第二個功能的好處是資料的複本數目降至最低，以及允許的資料直接儲存到類別的成員 (`CDaoRecordset`衍生的類別)。 此第二種機制是 MFC 用來繫結至資料成員中的方法`CDaoRecordset`衍生的類別。

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> 您的自訂 DFX 常式的用途

它是明顯來自必須能夠成功呼叫設定必要的資料結構中任何 DFX 函式實作的最重要作業。 在本討論`GetRows`。 有幾個的 DFX 函式必須也支援其他作業，但不為重要或複雜正確準備`GetRows`呼叫。

線上文件中會說明如何使用 DFX。 基本上，有兩個需求。 首先，必須新增成員至`CDaoRecordset`衍生的類別，針對每個繫結的欄位和參數。 遵循此`CDaoRecordset::DoFieldExchange`應該覆寫。 請注意，成員的資料型別是很重要。 它應該符合資料庫中欄位的資料，或至少可轉換成該類型。 例如在資料庫中，例如長整數的數值欄位可以一律轉換成文字並繫結至`CString`成員，但在資料庫中的文字欄位可能不一定會轉換成數值表示法，例如長整數和繫結至完整的整合er 成員。 DAO 和 Microsoft Jet 資料庫引擎負責轉換 （而非 MFC）。

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> DFX_Text 的詳細資料

如先前所述，解釋 DFX 是如何運作的最佳方式就是逐步的範例。 因此，透過內部`DFX_Text`應該能順利運作，有助於 DFX 至少有基本認識。

- `AddToParameterList`

   這項作業會建置 SQL**參數**子句 ("`Parameters <param name>, <param type> ... ;`」) 所需的 Jet。 每個參數是名為，而且型別 （如 RFX 呼叫中指定）。 請參閱函數`CDaoFieldExchange::AppendParamType`函式，以查看個別類型的名稱。 若是`DFX_Text`，使用的類型是**文字**。

- `AddToSelectList`

   建置 SQL**選取**子句。 這很直接，DFX 呼叫所指定的資料行名稱就是附加 (「`SELECT <column name>, ...`")。

- `BindField`

   最複雜的作業。 如先前所述這是 DAO 繫結結構會由`GetRows`設定。 中的程式碼，您可以看到`DFX_Text`的結構中的資訊類型包括使用的 DAO 類型 (**DAO_CHAR**或是**DAO_WCHAR**是`DFX_Text`)。 此外，使用的繫結的類型也會設定。 在先前章節`GetRows`中所述僅簡單地說，但仍不足以說明 MFC 使用的繫結的類型一律是直接處理繫結 (**DAOBINDING_DIRECT**)。 此外可變長度資料行繫結 (例如`DFX_Text`) 回呼繫結使用，因此 MFC 可以控制 記憶體配置和指定的位址是正確的長度。 這表示是 MFC 也始終會判斷 DAO"where"放置資料，因此直接繫結至成員變數。 繫結結構的其餘部分會填入之類的位址的記憶體配置回呼函式和資料行繫結 （繫結的資料行名稱） 的類型。

- `BindParam`

   這是簡單的作業呼叫`SetParamValue`參數成員中指定的參數值。

- `Fixup`

   填寫**NULL**每個欄位的狀態。

- `SetFieldNull`

   這項作業只能標記要為每個欄位狀態**NULL**並將成員變數的值設定為**PSEUDO_NULL**。

- `SetDirtyField`

   呼叫`SetFieldValue`每個欄位標示為已變更。

所有其餘的作業只會處理使用的資料快取。 資料快取是額外的緩衝區，用以簡化某些項目是目前記錄中的資料。 比方說，您可以自動偵測這項 「 中途 」 欄位。 它可以關閉完全或在欄位層級的線上文件所述。 緩衝區的實作會使用對應。 此對應來對應資料的動態配置的複本與 「 繫結 」 欄位的位址 (或`CDaoRecordset`衍生的資料成員)。

- `AllocCache`

   以動態方式配置的快取的欄位值，並將它加入至地圖。

- `FreeCache`

   刪除快取的欄位值，並將它從對應移除。

- `StoreField`

   將目前的欄位值複製到資料快取中。

- `LoadField`

   將快取的值複製到欄位成員中。

- `MarkForAddNew`

   檢查目前的欄位值是否不**NULL**並將其標示為中途如有必要。

- `MarkForEdit`

   比較目前的欄位值與資料快取，並標示為已變更，如有必要。

> [!TIP]
> 建立您的自訂 DFX 常式模型上現有的 DFX 常式，標準的資料類型。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
