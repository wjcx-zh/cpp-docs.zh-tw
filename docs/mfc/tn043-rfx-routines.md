---
title: TN043：RFX 常式
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 278351ad1cf81215f4c6033f4cff0b100adedf23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658857"
---
# <a name="tn043-rfx-routines"></a>TN043：RFX 常式

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示描述的資料錄欄位交換 (RFX) 架構。 它也會說明如何撰寫**RFX_** 程序。

## <a name="overview-of-record-field-exchange"></a>資料錄欄位交換的概觀

所有的資料錄集欄位函式已完成 c + + 程式碼。 沒有任何特殊的資源或 magic 巨集。 機制的核心是必須在每個衍生的資料錄集類別中覆寫虛擬函式。 在這種形式一律找到它：

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

特殊格式 AFX 註解允許 ClassWizard 來找出並編輯中這個函式的程式碼。 ClassWizard 與不相容的程式碼應該會位於特殊格式註解。

在上述範例中， \<recordset_exchange_field_type_call > 的格式為：

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

和\<recordset_exchange_function_call > 的格式為：

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

大部分**RFX_** 函式有三個引數，如上所示，但有部分 (例如`RFX_Text`和`RFX_Binary`) 有額外的選擇性引數。

多個**RFX_** 可能會包含在每個`DoDataExchange`函式。

請參閱 'afxdb.h' 的所有資料錄欄位交換常式隨 MFC 提供的清單。

資料錄集欄位的呼叫會註冊 （通常是資料成員） 的記憶體位置的方法來儲存欄位的資料`CMySet`類別。

## <a name="notes"></a>注意

資料錄集欄位函數的設計僅適用於`CRecordset`類別。 它們不是一般情況下使用的任何其他的 MFC 類別。

標準 c + + 建構函式中，通常在區塊中以設定初始值的資料`//{{AFX_FIELD_INIT(CMylSet)`和`//}}AFX_FIELD_INIT`註解。

每個**RFX_** 函式必須支援各種作業，範圍從封存的欄位，以準備進行編輯的欄位將傳回的欄位已變更的狀態。

每個呼叫的函式`DoFieldExchange`(例如`SetFieldNull`， `IsFieldDirty`)，並呼叫周圍初始化`DoFieldExchange`。

## <a name="how-does-it-work"></a>如何運作

您不需要了解下列，才能使用資料錄欄位交換。 不過，這在幕後的運作方式，將可協助您了解撰寫您自己的 exchange 程序。

`DoFieldExchange`成員函式，就像`Serialize`成員函式，它會負責取得或設定資料 （在此案例的資料行從 ODBC 查詢的結果） 以外部格式之間來回類別中的成員資料。 *PFX*參數是對進行資料交換內容，類似於*CArchive*參數`CObject::Serialize`。 *PFX* (`CFieldExchange`物件) 有作業指標，也就是類似，但的概括*CArchive*方向旗標。 RFX 函式可能要支援下列作業：

- `BindParam` 表示 ODBC 擷取參數資料的地方

- `BindFieldToColumn` 表示其中 ODBC 必須擷取/存款 outputColumn 資料

- `Fixup` ： 設定`CString/CByteArray`長度，則設定位元的 NULL 狀態

- `MarkForAddNew` -標示已變更，如果值已變更，因為呼叫 AddNew

- `MarkForUpdate` -標示已變更，如果值已變更，因為編輯呼叫

- `Name` — 附加欄位標示為已變更的欄位名稱

- `NameValue` — 附加"\<資料行名稱 > ="標示為已變更的欄位

- `Value` — 附加""後面接著分隔符號，例如 '、' 或 ' '

- `SetFieldDirty` ： 設定狀態位元已變更 （也就是已變更） 欄位

- `SetFieldNull` ： 設定欄位的 null 值，指出葒鷑糔磢

- `IsFieldDirty` -傳回值已變更的狀態位元

- `IsFieldNull` -傳回 null 狀態位元值

- `IsFieldNullable` -傳回 TRUE，如果欄位可以保留 NULL 值

- `StoreField` — 封存欄位值

- `LoadField` — 重新載入保存的欄位值

- `GetFieldInfoValue` — 在欄位上傳回的一般資訊

- `GetFieldInfoOrdinal` — 在欄位上傳回的一般資訊

## <a name="user-extensions"></a>使用者擴充功能

有數種方式來擴充預設 RFX 機制。 您可以

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

- 有`DoFieldExchange`成員函式有條件地包含其他 RFX 呼叫或任何其他有效的 c + + 陳述式。

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

若要撰寫您自己的自訂 RFX 函式，建議您複製現有 RFX 函式，並修改為您的用途。 選取要複製正確的 RFX，可以讓您的工作更輕鬆。 某些 RFX 函式會有一些特有的屬性，決定要複製時，您應該考慮到。

`RFX_Long` 和`RFX_Int`： 這些是最簡單的 RFX 函式。 資料值不需要任何特殊的解譯和資料大小固定的。

`RFX_Single` 和`RFX_Double`： 例如 RFX_Long 和 RFX_Int 上述，這些函式很簡單，並可廣泛使用的預設實作。 它們會儲存在 dbflt.cpp 而不是 dbrfx.cpp，不過，若要啟用 載入執行階段的時候才明確參考浮點程式庫。

`RFX_Text` 和`RFX_Binary`： 預先配置的靜態緩衝區，以便容納字串/二進位檔的詳細資訊，這兩個函數，並必須以 ODBC SQLBindCol 註冊這些緩衝區而不是註冊 （& v）。 因為這個緣故，這些兩個函式會有許多特殊情況撰寫程式碼。

`RFX_Date`: ODBC 傳回自己 TIMESTAMP_STRUCT 資料結構中的日期和時間資訊。 此函式會動態配置 TIMESTAMP_STRUCT 作為 「 proxy 」 來傳送和接收日期時間資料。 各種作業之間必須傳輸的日期和時間資訊的 c + +`CTime`物件和 TIMESTAMP_STRUCT proxy。 這變得非常複雜此函式相當大，但它是如何使用 proxy 來傳輸資料的理想範例。

`RFX_LongBinary`： 這是唯一的類別庫不會使用資料行繫結接收和傳送資料的 RFX 函式。 此函式會忽略 BindFieldToColumn 作業和相反地，修復作業期間，會配置儲存空間來保存內送 SQL_LONGVARCHAR 或 SQL_LONGVARBINARY 資料，則會執行到配置的儲存體擷取值的 SQLGetData 呼叫。 準備要將資料值送回資料來源 （例如名稱/值和值的作業），則此函數會使用 ODBC 的 DATA_AT_EXEC 功能。 請參閱[技術的附註 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md)如需有關使用 SQL_LONGVARBINARY 和 SQL_LONGVARCHARs。

在撰寫您自己**RFX_** 函式，您通常會使用`CFieldExchange::Default`實作指定的作業。 看看指定的作業的預設實作。 如果它不會執行此作業就需要撰寫您**RFX_** 函式，您可以委派給`CFieldExchange::Default`。 您可以看到呼叫的範例`CFieldExchange::Default`dbrfx.cpp 中

請務必呼叫`IsFieldType`RFX 函式，以及傳回，它會傳回 FALSE 時，立即開始。 這項機制會保留參數上執行的作業*outputColumns*，反之亦然 (例如呼叫`BindParam`上*outputColumn*)。 颾魤 ㄛ`IsFieldType`自動記錄的計數*outputColumns* (*m_nFields*) 以及參數 (*m_nParams*)。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
