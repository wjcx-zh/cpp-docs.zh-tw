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
ms.openlocfilehash: de9db2713a25b232bbd7f936958d1c10e96c511a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753175"
---
# <a name="cfieldexchange-class"></a>CFieldExchange 類別

支援資料庫類別使用的資料錄欄位交換 (RFX) 和大量資料錄欄位交換 (Bulk RFX) 常式。

## <a name="syntax"></a>語法

```
class CFieldExchange
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFieldExchange::場位型別](#isfieldtype)|如果當前操作適合更新的欄位類型,則返回非零。|
|[CFieldExchange:setField 類型](#setfieldtype)|指定紀錄集資料成員的類型 ( 欄位或參數 - 由以下所有對 RFX`SetFieldType`函數的呼叫, 直到下一次呼叫 。|

## <a name="remarks"></a>備註

`CFieldExchange`沒有基類。

如果要為自定義數據類型編寫數據交換例程,或者在實現批量行提取時,請使用此類;否則,您不會直接使用此類。 RFX 和批量 RFX 在記錄集物件的欄位數據成員和數據源上的當前記錄的相應欄位之間交換數據。

> [!NOTE]
> 如果您使用的是資料存取物件 (DAO) 類別,而不是開放資料庫連接 (ODBC) 類別,請使用類[CDaoFieldExchange。](../../mfc/reference/cdaofieldexchange-class.md) 有關詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

`CFieldExchange`物件提供進行記錄欄位交換或批量記錄欄位交換所需的上下文資訊。 `CFieldExchange`物件支援許多操作,包括綁定參數和欄位數據成員,以及在當前記錄的欄位上設置各種標誌。 RFX 和批量 RFX 操作在 中定義的類型類型的記錄**enum**集類數據成員**上**`CFieldExchange`執行。 可能的**欄位型態**值包括:

- `CFieldExchange::outputColumn`用於欄位數據成員。

- `CFieldExchange::inputParam`或`CFieldExchange::param`用於輸入參數數據成員。

- `CFieldExchange::outputParam`用於輸出參數數據成員。

- `CFieldExchange::inoutParam`用於輸入/輸出參數資料成員。

類的大多數成員函數和數據成員都用於編寫您自己的自定義 RFX 例程。 您將`SetFieldType`經常使用。 有關詳細資訊,請參閱[文章記錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)和[記錄集 (ODBC)。](../../data/odbc/recordset-odbc.md) 有關批量行提取的資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) 有關 RFX 和批量 RFX 全域函數的詳細資訊,請參閱此參考的 MFC 宏和全域部分中的[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CFieldExchange`

## <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange::場位型別

如果編寫自己的 RFX 函數,`IsFieldType`請在函數的開頭調用以確定是否可以對特定欄位`CFieldExchange::outputColumn`或參數 資料成員類型`CFieldExchange::inputParam``CFieldExchange::param`(a、 、、、`CFieldExchange::outputParam`或`CFieldExchange::inoutParam`) 執行當前操作。

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>參數

*pnField*<br/>
在此參數中返回欄位或參數數據成員的順序數。 此數字對應於[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)函數中的數據成員的順序。

### <a name="return-value"></a>傳回值

如果可以在當前欄位或參數類型上執行當前操作,則非零。

### <a name="remarks"></a>備註

遵循現有 RFX 函數的模型。

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange:setField 類型

您需要`SetFieldType`在記錄集類的[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)或[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)覆蓋中調用。

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>參數

*nFieldType*<br/>
中`enum FieldType``CFieldExchange`宣告的值可以是以下值之一:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>備註

對於現場數據成員,必須調用`SetFieldType`參數`CFieldExchange::outputColumn`, 後跟對 RFX 或批量 RFX 函數的調用。 如果尚未實現批量行提取,則 ClassWizard`SetFieldType`將此`DoFieldExchange`調用放在的欄位映射部分中。

如果參數化記錄集類,則必須在任何欄位映射節`SetFieldType`之外再次調用,然後對所有參數數據成員進行 RFX 調用。 每種類型的參數數據成員必須有自己的`SetFieldType`調用。 下表區分了可以傳遞給`SetFieldType`以表示類的參數資料成員的不同值:

|設定欄位型別參數值|參數資料成員的類型|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|輸入參數。 傳遞到記錄集的查詢或存儲過程的值。|
|`CFieldExchange::param` | 與`CFieldExchange::inputParam`相同。|
|`CFieldExchange::outputParam`|輸出參數。 記錄集存儲過程的返回值。|
|`CFieldExchange::inoutParam`|輸入/輸出參數。 傳入記錄集的存儲過程並從中返回的值。|

通常,與欄位資料成員或參數資料成員關聯的每組 RFX 函數呼叫之前都必須`SetFieldType`呼叫 。 每個`SetFieldType`調用的`SetFieldType`*nFieldType*參數標識調用後 RFX 函數調用表示的數據成員的類型。

有關處理輸出和輸入/輸出參數的詳細資訊,請參閱`CRecordset`成員函數[FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset)。 有關 RFX 和批量 RFX 函數的詳細資訊,請參閱主題[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。 有關批量行提取的相關信息,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>範例

此示例顯示對 RFX 函數的多個調用`SetFieldType`以及對 的附帶調用。 請注意,`SetFieldType``pFX`通過`CFieldExchange`指向 物件的指標調用。

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
