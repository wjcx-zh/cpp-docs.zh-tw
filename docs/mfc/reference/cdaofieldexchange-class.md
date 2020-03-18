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
ms.openlocfilehash: cfffebd16c3c1d62dc4084b962c22911e4b46ae5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420621"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 類別

支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。

DAO 受到 Office 2013 的支援。 DAO 3.6 是最後的版本，被視為已淘汰。

## <a name="syntax"></a>語法

```
class CDaoFieldExchange
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|如果目前的作業適用于要更新之欄位的類型，則傳回非零。|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|指定記錄集資料成員（資料行或參數）的類型，這是由所有後續呼叫 DFX 函數所表示，直到下一次呼叫 `SetFieldType`為止。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoFieldExchange：： m_nOperation](#m_noperation)|目前對記錄集之 `DoFieldExchange` 成員函式的呼叫所執行的 DFX 作業。|
|[CDaoFieldExchange：： m_prs](#m_prs)|執行 DFX 作業之記錄集的指標。|

## <a name="remarks"></a>備註

`CDaoFieldExchange` 沒有基類。

如果您要撰寫自訂資料類型的資料交換常式，請使用這個類別;否則，您將不會直接使用這個類別。 DFX 會在[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的欄位資料成員和資料來源上目前記錄的對應欄位之間交換資料。 DFX 會從資料來源和資料來源管理雙向的交換。 如需撰寫自訂 DFX 常式的相關資訊，請參閱[技術提示 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) 。

> [!NOTE]
>  DAO 資料庫類別與以開放式資料庫連接（ODBC）為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源。 一般而言，以 DAO 為基礎的 MFC 類別比以 ODBC 為基礎的 MFC 類別更有能力。 以 DAO 為基礎的類別可以透過自己的資料庫引擎來存取資料，包括透過 ODBC 驅動程式。 它們也支援資料定義語言（DDL）作業，例如透過類別加入資料表，而不需要自行呼叫 DAO。

> [!NOTE]
>  DAO 記錄欄位交換（DFX）與以 ODBC 為基礎的 MFC 資料庫類別（`CDatabase`、`CRecordset`）中的記錄欄位交換（RFX）非常類似。 如果您瞭解 RFX，就會發現使用 DFX 很容易。

`CDaoFieldExchange` 物件會提供要進行 DAO 記錄欄位結算所需的內容資訊。 `CDaoFieldExchange` 物件支援多項作業，包括系結參數和欄位資料成員，以及在目前記錄的欄位上設定各種旗標。 DFX 作業是在 `CDaoFieldExchange`的**列舉** **FieldType**所定義之類型的記錄集類別資料成員上執行。 可能的**FieldType**值為：

- 欄位資料成員的 `CDaoFieldExchange::outputColumn`。

- 參數資料成員的 `CDaoFieldExchange::param`。

[IsValidOperation](#isvalidoperation)成員函式是提供來撰寫您自己的自訂 DFX 常式。 您會在 CDaoRecordset 中經常使用[SetFieldType](#setfieldtype) [：:D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函式。 如需 DFX 全域函式的詳細資訊，請參閱[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。 如需針對您自己的資料類型撰寫自訂 DFX 常式的詳細資訊，請參閱[技術提示 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDaoFieldExchange`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

如果您撰寫自己的 DFX 函數，請在函式的開頭呼叫 `IsValidOperation`，以判斷是否可以在特定欄位資料成員類型（`CDaoFieldExchange::outputColumn` 或 `CDaoFieldExchange::param`）上執行目前的作業。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>傳回值

如果目前的作業適用于要更新之欄位的類型，則為非零。

### <a name="remarks"></a>備註

DFX 機制執行的某些作業僅適用于其中一個可能的欄位類型。 遵循現有的 DFX 函數模型。

如需撰寫自訂 DFX 常式的詳細資訊，請參閱[技術提示 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

##  <a name="m_noperation"></a>CDaoFieldExchange：： m_nOperation

識別要在與欄位交換物件相關聯的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件上執行的作業。

### <a name="remarks"></a>備註

`CDaoFieldExchange` 物件會針對記錄集提供一些不同的 DFX 作業內容。

> [!NOTE]
>  下列 MarkForAddNew 和 SetFieldNull 作業底下所述的 PSEUDONull 值是用來將欄位標記為 Null 的值。 DAO 記錄欄位交換器制（DFX）會使用此值來判斷哪些欄位已明確標示為 Null。 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)和[COleCurrency](../../mfc/reference/colecurrency-class.md)欄位不需要 PSEUDONull。

`m_nOperation` 的可能值為：

|作業|描述|
|---------------|-----------------|
|`AddToParameterList`|建立 SQL 語句的**PARAMETERS**子句。|
|`AddToSelectList`|建立 SQL 語句的**SELECT**子句。|
|`BindField`|將資料庫中的欄位系結至應用程式中的記憶體位置。|
|`BindParam`|設定記錄集查詢的參數值。|
|`Fixup`|設定欄位的 Null 狀態。|
|`AllocCache`|配置用來檢查記錄集中是否有「已變更」欄位的快取。|
|`StoreField`|將目前的記錄儲存至快取。|
|`LoadField`|還原記錄集中快取的資料成員變數。|
|`FreeCache`|釋放用來檢查記錄集中是否有「已變更」欄位的快取。|
|`SetFieldNull`|將欄位的狀態設定為 Null，並將值設為 PSEUDONull。|
|`MarkForAddNew`|將欄位標示為「已變更」（如果未 PSEUDONull）。|
|`MarkForEdit`|當欄位不符合快取時，將其標示為「已變更」。|
|`SetDirtyField`|設定標示為「已變更」的域值。|
|`DumpField`|傾印欄位的內容（僅限 debug）。|
|`MaxDFXOperation`|用於輸入檢查。|

##  <a name="m_prs"></a>CDaoFieldExchange：： m_prs

包含與 `CDaoFieldExchange` 物件相關聯之[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件的指標。

### <a name="remarks"></a>備註

##  <a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

呼叫 `CDaoRecordset` 類別的 `DoFieldExchange` 覆寫中的 `SetFieldType`。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>參數

*nFieldType*<br/>
**列舉 FieldType**的值（在 `CDaoFieldExchange`中宣告），可以是下列其中一項：

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>備註

一般來說，ClassWizard 會為您撰寫此呼叫。 如果您撰寫自己的函式，並使用 wizard 來撰寫您的 `DoFieldExchange` 函式，請在欄位對應外新增對您自己函數的呼叫。 如果您不使用此嚮導，將不會有欄位對應。 呼叫會先呼叫 DFX 函式，分別用於類別的每個欄位資料成員，並將欄位類型識別為 `CDaoFieldExchange::outputColumn`。

如果您將記錄集類別參數化，您應該為所有參數資料成員（在欄位對應外）新增 DFX 呼叫，並在這些呼叫前面加上 `SetFieldType`的呼叫。 傳遞值 `CDaoFieldExchange::param`。 （您可以改為使用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)並設定其參數值）。

一般而言，與欄位資料成員或參數資料成員相關聯的每個 DFX 函式呼叫群組，前面必須加上 `SetFieldType`的呼叫。 每個 `SetFieldType` 呼叫的*nFieldType*參數會識別依照 `SetFieldType` 呼叫的 DFX 函式呼叫所代表的資料成員類型。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)
