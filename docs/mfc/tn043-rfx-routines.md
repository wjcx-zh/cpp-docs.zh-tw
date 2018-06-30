---
title: 'TN043: RFX 常式 |Microsoft 文件'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RFX
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0c53ed2d1f1ab1a965a913287c8b5c171903518
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122759"
---
# <a name="tn043-rfx-routines"></a>TN043：RFX 常式

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示描述的資料錄欄位交換 (RFX) 架構。 它也會說明如何撰寫**RFX_** 程序。

## <a name="overview-of-record-field-exchange"></a>資料錄欄位交換的概觀

C + + 程式碼完成所有的資料錄集欄位函式。 沒有任何特殊的資源或 magic 巨集。 機制的核心是必須在每個衍生的資料錄集類別中覆寫虛擬函式。 它一律是找到這種形式：

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

特殊格式 AFX 註解允許 ClassWizard 找出並編輯這個函式中的程式碼。 ClassWizard 與不相容的程式碼應該會位於外部的特殊格式註解。

在上述範例中，< recordset_exchange_field_type_call > 的格式為：

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

而且 < recordset_exchange_function_call > 是下列格式：

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

大部分**RFX_** 函式有三個引數，如上所示，但有部分 (例如`RFX_Text`和`RFX_Binary`) 有額外的選擇性引數。

多個**RFX_** 可能會包含在每個`DoDataExchange`函式。

請參閱 'afxdb.h' 的所有資料錄欄位交換常式隨 MFC 提供的清單。

已註冊的記憶體位置 （通常是資料成員） 的方式，儲存的資料欄位的資料錄集欄位呼叫`CMySet`類別。

## <a name="notes"></a>注意

資料錄集欄位函數的設計僅適用於`CRecordset`類別。 它們不是由任何其他的 MFC 類別通常可使用。

起始值的資料在標準 c + + 建構函式，通常是在含有的區塊中設定`//{{AFX_FIELD_INIT(CMylSet)`和`//}}AFX_FIELD_INIT`註解。

每個**RFX_** 函式必須支援各種作業，範圍從傳回的欄位已變更狀態到封存中準備編輯欄位的欄位。

每個呼叫的函式`DoFieldExchange`(例如`SetFieldNull`， `IsFieldDirty`)，並呼叫周圍初始化`DoFieldExchange`。

## <a name="how-does-it-work"></a>它如何運作

您不需要了解下，若要使用資料錄欄位交換。 不過，這在幕後的運作方式，將可協助您了解撰寫自己的交換程序。

`DoFieldExchange`成員函式，就像`Serialize`成員函式，它會負責取得或設定資料，從中 （在此案例的資料行從 ODBC 查詢的結果） 以外部格式從/成員類別中的資料。 *PFX*參數已經進行資料交換的內容，類似於*CArchive*參數`CObject::Serialize`。 *PFX* (`CFieldExchange`物件) 有操作指標，也就是類似，但的一般化*CArchive*方向旗標。 RFX 函式可能需要支援下列作業：

- `BindParam` 表示 ODBC 擷取參數資料的地方

- `BindFieldToColumn` 表示其中 ODBC 必須擷取/存款 outputColumn 資料

- `Fixup` — 設定`CString/CByteArray`長度，會設定位元的 NULL 狀態

- `MarkForAddNew` -標示已變更，如果值已變更，因為呼叫 AddNew

- `MarkForUpdate` -標示已變更，如果值已變更，因為編輯呼叫

- `Name` — 附加欄位標示為已變更的欄位名稱

- `NameValue` — 附加"\<資料行名稱 > ="標示為已變更的欄位

- `Value` — 附加""後面接著分隔符號，例如 '、' 或 ' '

- `SetFieldDirty` — 設定狀態位元的中途 （也就是已變更） 欄位

- `SetFieldNull` — 設定狀態位元，指出欄位的 null 值

- `IsFieldDirty` -傳回值已變更的狀態位元

- `IsFieldNull` -傳回 null 狀態位元值

- `IsFieldNullable` -傳回 TRUE，如果欄位可以保存 NULL 值

- `StoreField` — 封存欄位值

- `LoadField` — 重新載入封存的欄位值

- `GetFieldInfoValue` — 在欄位上傳回的一般資訊

- `GetFieldInfoOrdinal` — 在欄位上傳回的一般資訊

## <a name="user-extensions"></a>使用者擴充功能

有幾種方式來擴充預設 RFX 機制。 您可以

- 加入新的資料類型。 例如: 

    ```cpp
    CBookmark
    ```

- 加入新的 exchange 程序 (RFX_)。

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- 具有`DoFieldExchange`成員函式有條件地包含其他 rfx 或任何其他有效的 c + + 陳述式。

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> 這類程式碼無法編輯 ClassWizard，應該用於只能之外的特殊格式註解。

## <a name="writing-a-custom-rfx"></a>撰寫自訂 RFX

若要撰寫您自己的自訂 RFX 函式，建議您複製現有的 RFX 函式，並修改您自己的用途。 選取要複製右 RFX，可讓您的工作更容易。 有些 RFX 函式有一些特有的屬性，決定要複製的目的地時，您應該考慮到。

`RFX_Long` 和`RFX_Int`： 這些是最簡單的 RFX 函式。 資料值不需要任何特殊的解譯和資料大小固定的。

`RFX_Single` 和`RFX_Double`： 像 RFX_Long RFX_Int 上述，這些函式是簡單且可廣泛使用的預設實作。 它們會儲存在 dbflt.cpp 而不是 dbrfx.cpp，不過，若要啟用載入執行階段的浮點程式庫的時候才明確參考。

`RFX_Text` 和`RFX_Binary`： 這兩個函數預先配置的靜態緩衝區來保存字串/二進位檔的詳細資訊，並必須向這些緩衝區 ODBC SQLBindCol 而不是註冊 （& s） 值。 因為這個緣故，這兩個函數有許多特殊的程式碼。

`RFX_Date`: ODBC 傳回自己 TIMESTAMP_STRUCT 資料結構中的日期和時間資訊。 此函式會動態配置 TIMESTAMP_STRUCT 作為 「 proxy 」 來傳送和接收日期時間資料。 各種作業之間必須傳輸的日期和時間資訊的 c + +`CTime`物件和 TIMESTAMP_STRUCT proxy。 這得相當大，此函式，但它是如何使用 proxy 來處理資料傳輸的良好範例。

`RFX_LongBinary`： 這是唯一的類別庫不使用來接收和傳送資料的資料行繫結的 RFX 函式。 此函式會忽略 BindFieldToColumn 作業並相反地，修復作業期間，會配置儲存空間來保存傳入 SQL_LONGVARCHAR 或 SQL_LONGVARBINARY 資料，然後執行配置的儲存體，擷取值的 SQLGetData 呼叫。 準備要將資料值送回資料來源 （例如名稱值和值的作業） 時，此函數會使用 ODBC 的 DATA_AT_EXEC 功能。 請參閱[技術附註 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)如需有關使用 SQL_LONGVARBINARY 和 SQL_LONGVARCHARs。

在撰寫您自己**RFX_** 函式，您通常能夠使用`CFieldExchange::Default`實作指定的作業。 查看問題中的作業預設實作。 如果執行作業您會撰寫您**RFX_** 函式，您可以委派給`CFieldExchange::Default`。 您可以看到的呼叫範例`CFieldExchange::Default`dbrfx.cpp 中

請務必呼叫`IsFieldType`在您的 RFX 函式，並將它傳回 FALSE 如果立即開始。 這項機制會保留參數上執行作業*outputColumns*，反之亦然 (例如呼叫`BindParam`上*outputColumn*)。 此外，`IsFieldType`自動追蹤的計數*outputColumns* (*m_nFields*) 以及參數之一 (*m_nParams*)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  
