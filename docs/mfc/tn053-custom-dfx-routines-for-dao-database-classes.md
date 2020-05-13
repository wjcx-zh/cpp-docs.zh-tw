---
title: TN053：DAO 資料庫類別的自訂 DFX 常式
ms.date: 09/17/2019
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
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365253"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053：DAO 資料庫類別的自訂 DFX 常式

> [!NOTE]
> DAO 與 Access 資料庫一起使用,並通過 Office 2013 支援。 DAO 3.6 是最終版本,它被視為過時版本。 視覺化C++環境和精靈不支援DAO(儘管包含DAO類,您仍可以使用它們)。 Microsoft 建議您將[OLE DB 範本](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)用於新專案。 您只應在維護現有應用程式時使用 DAO。

本技術說明描述了 DAO 記錄欄位交換 (DFX) 機制。 為了説明瞭解 DFX 例程中發生的情況`DFX_Text`,該 函數將作為示例詳細解釋。 作為本技術說明的其他資訊來源,您可以檢查其他單獨的 DFX 函數的代碼。 您可能不需要自定義 DFX 例程,因為可能需要自定義 RFX 例程(與 ODBC 資料庫類一起使用)。

本技術說明包含:

- DFX 概述

- 使用 DAO 記錄欄位交換並動態連結[的範例](#_mfcnotes_tn053_examples)

- [DFX 的工作原理](#_mfcnotes_tn053_how_dfx_works)

- [自訂 DFX 例程的作用](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text詳情](#_mfcnotes_tn053_details_of_dfx_text)

**DFX 概述**

DAO 記錄欄位交換機制 (DFX) 用於`CDaoRecordset`簡化使用 類時檢索和更新數據的過程。 使用`CDaoRecordset`類的數據成員簡化了該過程。 通過派生從`CDaoRecordset`,可以將數據成員添加到派生類中,表示表或查詢中的每個欄位。 這種"靜態綁定"機制很簡單,但它可能不是所有應用程式的首選數據提取/更新方法。 每次更改當前記錄時,DFX 都會檢索每個綁定欄位。 如果您正在開發一個性能敏感應用程式,在更改貨幣時不需要提取每個欄位,則透過`CDaoRecordset::GetFieldValue`「動態綁定」,`CDaoRecordset::SetFieldValue`並且可能是首選的數據訪問方法。

> [!NOTE]
> DFX 和動態綁定不是互斥的,因此可以使用靜態和動態綁定的混合使用。

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>範例 1 = 只使用 DAO 記錄欄位交換

(`CDaoRecordset`假設`CMySet`= 指定類別已開啟)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**範例 2 = 只使用動態的結合**

(假設使用`CDaoRecordset``rs`類別 ,並且它已經打開)

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

**範例 3 = 使用 DAO 記錄欄位交換並動態的結合**

(假設使用`CDaoRecordset`衍生式`emp`流覽員工資料)

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

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>DFX 的工作原理

DFX 機制的工作方式與 MFC ODBC 類使用的記錄欄位交換 (RFX) 機制類似。 DFX 和 RFX 的原則相同,但存在許多內部差異。 DFX 函數的設計使幾乎所有代碼都由各個 DFX 例程共用。 在最高級別的DFX只做幾件事。

- 如有必要,DFX 構造 SQL **SELECT**子句和 SQL**參數S**子句。

- DFX 構造`GetRows`DAO 函數使用的綁定結構(稍後將對此進行更多討論)。

- DFX 管理用於檢測髒欄位的數據緩衝區(如果使用雙緩衝)

- DFX 管理**NULL**和 DIRTY 狀態陣列 **,** 並在必要時在更新時設定值。

DFX 機制的核心`CDaoRecordset`是 派生類的`DoFieldExchange`功能。 此函數調度對適當操作類型的單個 DFX 函數的調用。 在調用`DoFieldExchange`內部 MFC 函數之前,將設置操作類型。 下面的清單顯示了各種操作類型和簡要說明。

|作業|描述|
|---------------|-----------------|
|`AddToParameterList`|產生參數子句|
|`AddToSelectList`|產生 SELECT 子句|
|`BindField`|設定繫結結構|
|`BindParam`|設定參數值|
|`Fixup`|設定 NULL 狀態|
|`AllocCache`|為臟檢查分配快取|
|`StoreField`|將目前記錄儲存到快取|
|`LoadField`|將快取回復到成員值|
|`FreeCache`|釋放快取|
|`SetFieldNull`|將欄位狀態&值設定為 NULL|
|`MarkForAddNew`|將欄位標記為髒,如果不是「無效」則|
|`MarkForEdit`|如果欄位與快取不匹配,則髒標記欄位|
|`SetDirtyField`|設定標記為髒的欄位值|

在下一節中,將更詳細地解釋 每個操作`DFX_Text`。

瞭解 DAO 記錄欄位交換過程的最重要特徵是`GetRows``CDaoRecordset`它使用 物件的函數。 DAO`GetRows`函數可以通過多種方式工作。 本技術說明僅簡要說明`GetRows`,因為它超出了本技術說明的範圍。
DAO`GetRows`可以以多種方式工作。

- 它可以一次獲取多個記錄和多個數據欄位。 這允許更快的數據訪問,處理大型數據結構的複雜性,並相應偏移到每個欄位和結構中的每個數據記錄。 MFC不會利用此多個記錄提取機制。

- 另一`GetRows`種方法是允許程式師為一個數據記錄為每個欄位的檢索數據指定綁定位址。

- DAO 還將"回撥"到調用方中,用於變數長度列,以便允許調用方分配記憶體。 第二個功能的好處是最大限度地減少數據拷貝的數量,並允許將數據直接存儲到類的成員(`CDaoRecordset`派生類)。 第二種機制是 MFC 用於綁定到派生`CDaoRecordset`類中 的數據成員的方法。

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>自訂 DFX 例程的作用

從這個討論中可以明顯看出,任何DFX函數中實現的最重要操作必須是能夠設置所需的數據結構才能成功調用`GetRows`。 DFX 函數還必須支持許多其他操作,但沒有一個操作像正確`GetRows`準備 調用那樣重要或複雜。

在線文檔中介紹了 DFX 的使用。 基本上,有兩個要求。 首先,必須將成員添加到每個綁定`CDaoRecordset`欄位和參數的派生類中。 之後`CDaoRecordset::DoFieldExchange`應重寫。 請注意,成員的數據類型很重要。 它應該匹配資料庫中的欄位的數據,或者至少可轉換為該類型。 例如,資料庫中的數位欄位(如長整數)始終可以轉換為文本並綁定到`CString`成員,但資料庫中的文本欄位不一定轉換為數位表示形式,如長整數並綁定到長整數成員。 DAO 和 Microsoft Jet 資料庫引擎負責轉換(而不是 MFC)。

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>DFX_Text詳情

如前所述,解釋 DFX 工作原理的最佳方法是通過示例工作。 為此,通過內部`DFX_Text`應很好地説明提供對DFX的基本理解。

- `AddToParameterList`

   此操作將生成 Jet 所需的`Parameters <param name>, <param type> ... ;`SQL **PARAMETERS**子句("")。 每個參數都命名和鍵入(如 RFX 調用中指定)。 請參閱函數`CDaoFieldExchange::AppendParamType`函數以查看各個類型的名稱。 在`DFX_Text`的情況下,使用的類型是**文字**。

- `AddToSelectList`

   生成 SQL **SELECT**子句。 這是相當直接的,因為 DFX 調用指定的列名稱只是附加 ("")。`SELECT <column name>, ...`

- `BindField`

   最複雜的操作。 如前所述,這是設置所使用的`GetRows`DAO 綁定結構的位置。 正如您在`DFX_Text`結構中的資訊型態中的代碼看到的,包括所使用的 DAO 型態**DAO_CHAR**(在`DFX_Text`DAO_CHAR或**DAO_WCHAR**的情況下 。 此外,還設置了使用的綁定類型。 在前面的一節中`GetRows`只簡要地描述了這一點,但足以說明 MFC 使用的綁定類型始終是直接位址綁定 **(DAOBINDING_DIRECT**)。 此外,還使用可變長度列綁定(如`DFX_Text`) 回調綁定,以便 MFC 可以控制記憶體分配並指定正確長度的位址。 這意味著 MFC 始終可以告訴 DAO"將數據放在何處",從而允許直接綁定到成員變數。 綁定結構的其餘部分填充了記憶體分配回調函數的位址和列綁定的類型(按列名稱綁定) 之類的內容。

- `BindParam`

   這是一個簡單的操作,`SetParamValue`呼叫參數成員中指定的參數值。

- `Fixup`

   填寫每個欄位的**NULL**狀態。

- `SetFieldNull`

   此操作只會將每個欄位狀態標記為**NULL,** 並將成員變數的值**設定為PSEUDO_NULL**。

- `SetDirtyField`

   調用`SetFieldValue`標記為臟的每個欄位。

所有剩餘的操作僅處理使用數據緩存。 數據緩存是當前記錄中數據的額外緩衝區,用於使某些內容更簡單。 例如,可以自動檢測"臟"欄位。 如在線文檔中所述,它可以完全關閉,也可以在現場級別關閉。 緩衝區的實現使用映射。 此映射用於將動態分配的數據副本與"綁定"欄位(或`CDaoRecordset`派生資料成員)的地址進行匹配。

- `AllocCache`

   動態分配緩存的欄位值並將其添加到地圖中。

- `FreeCache`

   刪除快取的欄位值並將其從映射中刪除。

- `StoreField`

   將當前欄位值複製到數據緩存中。

- `LoadField`

   將緩存的值複製到欄位成員中。

- `MarkForAddNew`

   檢查目前欄位值是否為非**NULL,** 並在必要時將其標記為髒。

- `MarkForEdit`

   將當前欄位值與數據緩存進行比較,並在必要時標記臟值。

> [!TIP]
> 在現有 DFX 例程上為標準數據類型建模自定義 DFX 例程。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
