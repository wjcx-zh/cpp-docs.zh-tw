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
ms.openlocfilehash: 6dde96520d9472726da86f8da295770cccc5d42c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303441"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053：DAO 資料庫類別的自訂 DFX 常式

> [!NOTE]
>  DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。 視覺C++環境和嚮導不支援 dao （雖然包含 dao 類別，但您仍然可以使用它們）。 Microsoft 建議您針對新專案使用 [OLE DB 樣板](../data/oledb/ole-db-templates.md)或是 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)。 您應該只在維護現有的應用程式時使用 DAO。

本技術提示說明 DAO 記錄欄位交換（DFX）機制。 為了協助您瞭解 DFX 常式中發生什麼情況，`DFX_Text` 函式將詳細說明為範例。 如需此技術提示的其他資訊來源，您可以檢查其他個別 DFX 函數的程式碼。 您可能不需要經常有自訂的 DFX 常式，因為您可能需要自訂的 RFX 常式（與 ODBC 資料庫類別搭配使用）。

此技術注意事項包含：

- DFX 總覽

- 使用 DAO 記錄欄位交換和動態繫結的[範例](#_mfcnotes_tn053_examples)

- [DFX 的運作方式](#_mfcnotes_tn053_how_dfx_works)

- [您的自訂 DFX 常式執行的工作](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [DFX_Text 的詳細資料](#_mfcnotes_tn053_details_of_dfx_text)

**DFX 總覽**

DAO 記錄欄位交換器制（DFX）是用來在使用 `CDaoRecordset` 類別時，簡化抓取和更新資料的程式。 此程式會使用 `CDaoRecordset` 類別的資料成員來簡化。 藉由從 `CDaoRecordset`衍生，您可以將資料成員加入至代表資料表或查詢中每個欄位的衍生類別。 這種「靜態系結」機制很簡單，但可能不是所有應用程式的資料提取/更新方法。 每當目前的記錄變更時，DFX 會抓取每個系結的欄位。 如果您正在開發不需要在變更貨幣時提取每個欄位的效能相關應用程式，則透過 `CDaoRecordset::GetFieldValue` 和 `CDaoRecordset::SetFieldValue` 的「動態系結」可能是選擇的資料存取方法。

> [!NOTE]
>  DFX 和動態繫結不是互斥的，因此可以使用靜態和動態系結的混合式使用。

## <a name="_mfcnotes_tn053_examples"></a>範例1—僅使用 DAO 記錄欄位交換

（假設 `CDaoRecordset`，衍生類別 `CMySet` 已開啟）

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**範例 2-僅使用動態繫結**

（假設使用 `CDaoRecordset` 類別，`rs`，而且已開啟）

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

**範例3：使用 DAO 記錄欄位交換和動態繫結**

（假設您使用 `emp`的 `CDaoRecordset`衍生類別來流覽員工資料）

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a>DFX 的運作方式

DFX 機制的運作方式與 MFC ODBC 類別所使用的記錄欄位交換（RFX）機制類似。 DFX 和 RFX 的原則相同，但有許多內部差異。 DFX 函式的設計是為了讓所有程式碼幾乎都是由個別的 DFX 常式所共用。 最高層級的 DFX 只會執行幾項工作。

- 必要時，DFX 會建立 SQL **SELECT**子句和 sql**參數**子句。

- DFX 會建立 DAO 的 `GetRows` 函式所使用的系結結構（稍後會詳細說明）。

- DFX 會管理用來偵測中途欄位的資料緩衝區（如果正在使用雙重緩衝）

- DFX 會管理**Null**和已**變更狀態陣列，並**在更新時設定值。

DFX 機制的核心是 `CDaoRecordset` 衍生類別的 `DoFieldExchange` 函數。 此函式會將呼叫分派至適當運算類型的個別 DFX 函數。 在呼叫之前 `DoFieldExchange` 內部 MFC 函式會設定作業類型。 下列清單顯示各種作業類型和簡短描述。

|運算|描述|
|---------------|-----------------|
|`AddToParameterList`|Build PARAMETERS 子句|
|`AddToSelectList`|組建 SELECT 子句|
|`BindField`|設定系結結構|
|`BindParam`|設定參數值|
|`Fixup`|設定 Null 狀態|
|`AllocCache`|配置用於中途檢查的快取|
|`StoreField`|將目前的記錄儲存至快取|
|`LoadField`|將快取還原至成員值|
|`FreeCache`|釋放快取|
|`SetFieldNull`|將欄位狀態 & 值設定為 Null|
|`MarkForAddNew`|如果不是虛擬 Null，則將欄位標示為已變更|
|`MarkForEdit`|當不符合快取時將欄位標示為已變更|
|`SetDirtyField`|設定標示為已變更的域值|

在下一節中，將會更詳細地說明每項作業的 `DFX_Text`。

若要瞭解 DAO 記錄欄位交換程式，最重要的功能就是它會使用 `CDaoRecordset` 物件的 `GetRows` 功能。 DAO `GetRows` 函式可以透過數種方式運作。 本技術提示只會簡短描述 `GetRows`，因為它超出此技術提示的範圍。
DAO `GetRows` 可以透過數種方式來工作。

- 它可以一次提取多個記錄和多個資料欄位。 這可讓您更快速地存取資料，而複雜的方式是處理大型資料結構和每個欄位的適當位移，以及結構中每筆資料的記錄。 MFC 不會利用這個多重記錄提取機制。

- `GetRows` 可以使用的另一種方式，是讓程式設計人員針對一筆資料記錄，為每個欄位的已抓取資料指定系結位址。

- DAO 也會在 [可變長度] 資料行的呼叫端中「回呼」，以便讓呼叫者可以配置記憶體。 第二個功能的優點是將資料的複本數目減至最少，並允許將資料直接儲存到類別的成員（`CDaoRecordset` 衍生類別）。 第二個機制是 MFC 用來系結至 `CDaoRecordset` 衍生類別中之資料成員的方法。

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>您的自訂 DFX 常式執行的工作

這在這項討論中很明顯，因為在任何 DFX 函式中執行的最重要作業必須能夠設定必要的資料結構，才能成功呼叫 `GetRows`。 DFX 函數也必須支援許多其他作業，但不像正確地準備 `GetRows` 呼叫一樣重要或複雜。

線上檔中會描述 DFX 的使用方式。 基本上，有兩個需求。 首先，必須將成員新增至每個系結欄位和參數的 `CDaoRecordset` 衍生類別中。 遵循此 `CDaoRecordset::DoFieldExchange` 應該會遭到覆寫。 請注意，成員的資料類型很重要。 它應該符合資料庫中欄位的資料，或至少可以轉換成該類型。 例如，資料庫中的數值欄位（例如長整數）一律可以轉換成文字，並系結至 `CString` 成員，但是資料庫中的文字欄位可能不一定會轉換成數值表示，例如長整數，並系結至長整數成員。 DAO 和 Microsoft Jet 資料庫引擎負責轉換（而不是 MFC）。

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>DFX_Text 的詳細資料

如先前所述，說明 DFX 運作方式的最佳方式，是透過範例來運作。 為了達到此目的，`DFX_Text` 的內部工作應該非常妥善，以協助至少提供對 DFX 的基本瞭解。

- `AddToParameterList`

   此操作會建立 Jet 所需的 SQL**參數**子句（"`Parameters <param name>, <param type> ... ;`"）。 每個參數的名稱都是和類型（如 RFX 呼叫中所指定）。 請參閱函數 `CDaoFieldExchange::AppendParamType` 函式，以查看個別類型的名稱。 在 `DFX_Text`的情況下，使用的類型是**文字**。

- `AddToSelectList`

   建立 SQL **SELECT**子句。 這相當簡單，因為 DFX 呼叫所指定的資料行名稱只會附加（"`SELECT <column name>, ...`"）。

- `BindField`

   最複雜的作業。 如先前所述，這是設定 `GetRows` 所使用之 DAO 系結結構的位置。 您可以從中的程式碼看到 `DFX_Text` 結構中的資訊類型包括使用的 DAO 類型（**DAO_CHAR**或 `DFX_Text`的案例中**DAO_WCHAR** ）。 此外，也會設定所使用的系結類型。 在先前的章節中，`GetRows` 只是簡短說明，但它足以說明 MFC 使用的系結類型一律是直接位址系結（**DAOBINDING_DIRECT**）。 此外，也會使用可變長度的資料行系結（例如 `DFX_Text`）回呼系結，讓 MFC 可以控制記憶體配置並指定正確長度的位址。 這表示 MFC 一律可以告訴 DAO 「where」來放置資料，因而允許直接系結至成員變數。 系結結構的其餘部分會以記憶體配置回呼函式的位址以及資料行系結的類型（依資料行名稱系結）填入。

- `BindParam`

   這是一個簡單的作業，會使用參數成員中指定的參數值來呼叫 `SetParamValue`。

- `Fixup`

   填入每個欄位的**Null**狀態。

- `SetFieldNull`

   這項作業只會將每個欄位狀態標示為**Null** ，並將成員變數的值設定為**PSEUDO_Null**。

- `SetDirtyField`

   針對每個標示為已變更的欄位呼叫 `SetFieldValue`。

所有剩餘的作業只會處理使用資料快取。 資料快取是目前記錄中資料的額外緩衝區，用來簡化特定專案。 例如，可以自動偵測「已變更」欄位。 如線上檔中所述，您可以完全或在欄位層級關閉它。 緩衝區的執行會利用對應。 這個對應用來比對動態配置的資料複本與「系結」欄位的位址（或 `CDaoRecordset` 衍生的資料成員）。

- `AllocCache`

   動態配置快取域值，並將其新增至地圖。

- `FreeCache`

   刪除快取的域值，並將它從對應中移除。

- `StoreField`

   將目前的域值複製到資料快取。

- `LoadField`

   將快取的值複製到欄位成員。

- `MarkForAddNew`

   檢查目前的域值是否為非**Null** ，並在必要時將其標示為已變更。

- `MarkForEdit`

   比較目前的域值與資料快取，並視需要將其標示為已變更。

> [!TIP]
> 針對標準資料類型，在現有的 DFX 常式上建立自訂 DFX 常式的模型。

## <a name="see-also"></a>請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
