---
title: CDaoFieldExchange 類別
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: e1ce6e13b9c6045881cc0bb4114a6e11d58365c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368984"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 類別

支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。

通過 Office 2013 支援 DAO。 DAO 3.6 是最終版本,它被視為過時版本。

## <a name="syntax"></a>語法

```
class CDaoFieldExchange
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDao現場交易:有效操作](#isvalidoperation)|如果當前操作適合更新的欄位類型,則返回非零。|
|[CDao現場交換::集場類型](#setfieldtype)|指定記錄集資料成員的類型 ( 列或參數 - 由對 DFX 函數`SetFieldType`的所有後續調用,直到 下一次調用 DFX 函數為止。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDao現場交易:m_nOperation](#m_noperation)|當前對記錄集成員函數的調用正在執行的`DoFieldExchange`DFX 操作。|
|[CDao現場交易:m_prs](#m_prs)|指向正在對其中執行 DFX 操作的記錄集的指標。|

## <a name="remarks"></a>備註

`CDaoFieldExchange`沒有基類。

如果要為自定義數據類型編寫數據交換例程,請使用此類;否則,您不會直接使用此類。 DFX 在[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的欄位數據成員和數據來源上的當前記錄的相應欄位之間交換數據。 DFX 從數據源到數據源,雙向管理交換。 有關編寫自定義 DFX 例程的資訊[,請參閱技術說明 53。](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)

> [!NOTE]
> DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 您仍可以使用 DAO 類存取 ODBC 資料來源。 通常,基於 DAO 的 MFC 類比基於 ODBC 的 MFC 類更有能力。 基於 DAO 的類可以通過自己的資料庫引擎訪問數據,包括透過 ODBC 驅動程式。 它們還支援數據定義語言 (DDL) 操作,例如透過類添加表,而不必自己調用 DAO。

> [!NOTE]
> DAO 記錄欄位交換 (DFX) 與基於 ODBC 的`CDatabase`MFC 資料庫`CRecordset`類 () 中的記錄欄位 交換 (RFX) 非常相似。 如果您瞭解 RFX,您會發現使用 DFX 很容易。

`CDaoFieldExchange`物件提供進行DAO記錄欄位交換所需的上下文資訊。 `CDaoFieldExchange`物件支援許多操作,包括綁定參數和欄位數據成員,以及在當前記錄的欄位上設置各種標誌。 DFX 操作在 中定義的**類型**類型的記錄集類數據**成員上**`CDaoFieldExchange`執行。 可能的**欄位型態**值包括:

- `CDaoFieldExchange::outputColumn`用於欄位數據成員。

- `CDaoFieldExchange::param`用於參數數據成員。

[IsValid操作](#isvalidoperation)成員函數用於編寫您自己的自定義 DFX 例程。 您將在[CDaoRecordset::D oFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)功能中經常使用[SetFieldType。](#setfieldtype) 有關 DFX 全域函數的詳細資訊,請參閱[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。 有關為您自己的數據類型編寫自定義 DFX 例程的資訊,請參閱[技術說明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDaoFieldExchange`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDao現場交易:有效操作

如果編寫自己的 DFX 函數,`IsValidOperation`請在函數的開頭調用以確定是否可以對特定欄位數據成員類型`CDaoFieldExchange::outputColumn`(a 或 a `CDaoFieldExchange::param`) 執行當前操作。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>傳回值

如果當前操作適合更新的欄位類型,則非零。

### <a name="remarks"></a>備註

DFX 機制執行的某些操作僅適用於可能欄位類型之一。 遵循現有 DFX 函數的模型。

有關編寫自定義 DFX 例程的其他資訊,請參閱[技術說明 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDao現場交易:m_nOperation

標識要在與字段交換物件關聯的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件上執行的操作。

### <a name="remarks"></a>備註

該`CDaoFieldExchange`物件為記錄集中的許多不同的 DFX 操作提供上下文。

> [!NOTE]
> 下面的 MarkForAddNew 和 SetFieldNull 操作下描述的 PSEUDONULL 值是用於標記欄位 Null 的值。 DAO 記錄欄位交換機制 (DFX) 使用此值來確定已顯式標記為 Null 的欄位。 [COleDateTime 和](../../atl-mfc-shared/reference/coledatetime-class.md) [COle 貨幣](../../mfc/reference/colecurrency-class.md)欄位不需要 PSEUDONULL。

的可能`m_nOperation`值為:

|作業|描述|
|---------------|-----------------|
|`AddToParameterList`|生成 SQL 語句的**PARAMETERS**子句。|
|`AddToSelectList`|生成 SQL 語句的**SELECT**子句。|
|`BindField`|將資料庫中的欄位綁定到應用程式中的記憶體位置。|
|`BindParam`|為記錄集的查詢設置參數值。|
|`Fixup`|設定欄位的 Null 狀態。|
|`AllocCache`|分配用於檢查記錄集中的「臟」欄位的緩存。|
|`StoreField`|將當前記錄保存到緩存中。|
|`LoadField`|還原記錄集中的緩存數據成員變數。|
|`FreeCache`|釋放用於檢查記錄集中的「臟」欄位的緩存。|
|`SetFieldNull`|將欄位的狀態設置為"空",並將值設置為 PSEUDONULL。|
|`MarkForAddNew`|標記為欄位"髒",如果不是 PSEUDONULL。|
|`MarkForEdit`|如果欄位與緩存不匹配,則標記它們「髒」。。|
|`SetDirtyField`|設置標記為「臟」的欄位值。|
|`DumpField`|轉儲欄位的內容(僅限調試)。|
|`MaxDFXOperation`|用於輸入檢查。|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDao現場交易:m_prs

包含指向與`CDaoFieldExchange`該物件關聯的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDao現場交換::集場類型

在`SetFieldType``CDaoRecordset`類的`DoFieldExchange`重寫中調用。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>參數

*nFieldType*<br/>
**枚舉欄位類型**的值 ,`CDaoFieldExchange`在 中 聲明,可以是以下任一值:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>備註

通常,ClassWizard 會為您編寫此話務。 如果您編寫自己的函數並使用嚮導編寫函數`DoFieldExchange`,請在欄位映射之外向自己的函數添加調用。 如果不使用嚮導,則沒有欄位映射。 呼叫之前對 DFX 函數的呼叫(針對類別的每個欄位資料成員一個),並將欄位類型`CDaoFieldExchange::outputColumn`標識為 。

如果對記錄集類進行參數化,則應為所有參數數據成員(欄位映射外部)添加 DFX 調用,並在調用 的這些調`SetFieldType`用之前添加 DFX 調用。 傳遞值`CDaoFieldExchange::param`。 (您可以改用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)並設置其參數值。

通常,與字段數據成員或參數數據成員關聯的每組 DFX 函數調用之前都`SetFieldType`必須對調用。 每個`SetFieldType`調用的`SetFieldType`*nFieldType*參數標識調用後 DFX 函數調用表示的數據成員的類型。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)
