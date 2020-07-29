---
title: CFieldExchange 類別
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: d10bfc436297a5f861f17843007347dcef9e58ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212471"
---
# <a name="cfieldexchange-class"></a>CFieldExchange 類別

支援資料庫類別使用的資料錄欄位交換 (RFX) 和大量資料錄欄位交換 (Bulk RFX) 常式。

## <a name="syntax"></a>語法

```
class CFieldExchange
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|如果目前的作業適用于要更新之欄位的類型，則傳回非零。|
|[CFieldExchange::SetFieldType](#setfieldtype)|指定記錄集資料成員（資料行或參數）的類型，這是由所有下列 RFX 函式呼叫所表示，直到下一次呼叫為止 `SetFieldType` 。|

## <a name="remarks"></a>備註

`CFieldExchange`沒有基類。

如果您要撰寫自訂資料類型的資料交換常式，或在執行大量資料列提取時，請使用這個類別。否則，您將不會直接使用這個類別。 RFX 和 Bulk RFX 會在記錄集物件的欄位資料成員和資料來源上目前記錄的對應欄位之間交換資料。

> [!NOTE]
> 如果您使用的是資料存取物件（DAO）類別，而不是開放式資料庫連接（ODBC）類別，請改用 [類別[CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) ]。 如需詳細資訊，請參閱文章[總覽：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

`CFieldExchange`物件會提供要進行記錄欄位交換或大量記錄欄位結算所需的內容資訊。 `CFieldExchange`物件支援多項作業，包括系結參數和欄位資料成員，以及在目前記錄的欄位上設定各種旗標。 RFX 和 Bulk RFX 作業是針對 **`enum`** 中**FieldType**所定義之類型的記錄集類別資料成員來執行 `CFieldExchange` 。 可能的**FieldType**值為：

- `CFieldExchange::outputColumn`適用于欄位資料成員。

- `CFieldExchange::inputParam`或 `CFieldExchange::param` 用於輸入參數資料成員。

- `CFieldExchange::outputParam`適用于輸出參數資料成員。

- `CFieldExchange::inoutParam`針對輸入/輸出參數資料成員。

大部分類別的成員函式和資料成員都是提供來撰寫您自己的自訂 RFX 常式。 您會 `SetFieldType` 經常使用。 如需詳細資訊，請參閱[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)和[記錄集（ODBC）](../../data/odbc/recordset-odbc.md)文章。 如需大量資料列提取的詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 如需 RFX 和 Bulk RFX 全域函式的詳細資訊，請參閱此參考的 MFC 宏和 Globals 一節中的[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CFieldExchange`

## <a name="requirements"></a>需求

**標頭：** afxdb。h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange::IsFieldType

如果您撰寫自己的 RFX 函式，請在函式 `IsFieldType` 的開頭呼叫，以判斷是否可以在特定欄位或參數資料成員類型（ `CFieldExchange::outputColumn` 、 `CFieldExchange::inputParam` 、、 `CFieldExchange::param` `CFieldExchange::outputParam` 或 `CFieldExchange::inoutParam` ）上執行目前的運算。

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>參數

*pnField*<br/>
此參數中會傳回欄位或參數資料成員的連續數位。 這個數位對應于[CRecordset：:D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[CRecordset：:D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函數中的資料成員順序。

### <a name="return-value"></a>傳回值

如果目前的作業可以在目前的欄位或參數類型上執行，則為非零值。

### <a name="remarks"></a>備註

遵循現有 RFX 函數的模型。

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange::SetFieldType

您需要 `SetFieldType` 在記錄集類別的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)覆寫中呼叫。

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>參數

*nFieldType*<br/>
的值 `enum FieldType` ，在中宣告 `CFieldExchange` ，它可以是下列其中一項：

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>備註

對於欄位資料成員，您必須 `SetFieldType` 使用的參數呼叫 `CFieldExchange::outputColumn` ，然後再呼叫 RFX 或 Bulk RFX 函數。 如果您尚未執行大量資料列提取，則 ClassWizard 會在的 `SetFieldType` [欄位對應] 區段中，為您放置此呼叫 `DoFieldExchange` 。

如果您將記錄集類別參數化，您必須在 `SetFieldType` 任何欄位對應區段外再次呼叫，後面接著所有參數資料成員的 RFX 呼叫。 每種類型的參數資料成員都必須有自己的 `SetFieldType` 呼叫。 下表區分您可以傳遞給的不同值， `SetFieldType` 以代表您類別的參數資料成員：

|SetFieldType 參數值|參數資料成員的類型|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|輸入參數。 傳遞至記錄集查詢或預存程式的值。|
|`CFieldExchange::param` | 與相同 `CFieldExchange::inputParam` 。|
|`CFieldExchange::outputParam`|輸出參數。 記錄集之預存程式的傳回值。|
|`CFieldExchange::inoutParam`|輸入/輸出參數。 傳入並從記錄集的預存程式傳回的值。|

一般而言，與欄位資料成員或參數資料成員相關聯的每個 RFX 函式呼叫群組，前面都必須呼叫 `SetFieldType` 。 每個呼叫的*nFieldType*參數都會 `SetFieldType` 識別遵循呼叫之 RFX 函式呼叫所代表的資料成員類型 `SetFieldType` 。

如需處理輸出和輸入/輸出參數的詳細資訊，請參閱成員函式 `CRecordset` [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 如需 RFX 和 Bulk RFX 函數的詳細資訊，請參閱主題[記錄欄位交換](../../mfc/reference/record-field-exchange-functions.md)函式。 如需大量資料列提取的相關資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>範例

這個範例會示範數個對 RFX 函式的呼叫，以及伴隨的呼叫 `SetFieldType` 。 請注意， `SetFieldType` 會透過 `pFX` 物件的指標呼叫 `CFieldExchange` 。

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
