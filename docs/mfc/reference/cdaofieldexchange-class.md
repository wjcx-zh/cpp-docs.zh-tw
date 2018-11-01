---
title: CDaoFieldExchange 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: ef88486d14ade1d5871d614069dc1c202d6ad159
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654216"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 類別

支援 DAO 資料庫類別使用的 DAO 資料錄欄位交換 (DFX) 常式。

## <a name="syntax"></a>語法

```
class CDaoFieldExchange
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|傳回非零值，如果目前的作業是適當的更新之欄位的類型。|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|指定資料錄集的資料成員的型別 — 資料行或參數-由 DFX 函式的所有後續呼叫，直到下次呼叫`SetFieldType`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|DFX 作業正在執行的資料錄集的目前呼叫`DoFieldExchange`成員函式。|
|[CDaoFieldExchange::m_prs](#m_prs)|資料錄集的 DFX 執行作業指標。|

## <a name="remarks"></a>備註

`CDaoFieldExchange` 沒有基底類別。

使用這個類別，如果您要撰寫自訂資料類型; 資料交換常式否則，您不會直接使用這個類別。 DFX 之間交換資料的欄位資料成員您[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件和資料來源上目前的記錄之對應欄位。 DFX 會管理這兩個方向的交換，從資料來源和資料來源。 請參閱[技術的附註 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)撰寫自訂 DFX 常式相關資訊。

> [!NOTE]
>  DAO 資料庫類別是開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別有所區別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別存取 ODBC 資料來源。 一般情況下，根據 DAO MFC 類別是更有能力比 ODBC 為基礎的 MFC 類別。 DAO 類別可以存取資料，包括透過 ODBC 驅動程式，透過自己的資料庫引擎。 它們也支援資料定義語言 (DDL) 作業，例如加入資料表透過而不必自行呼叫 DAO 類別。

> [!NOTE]
>  DAO 資料錄欄位交換 (DFX) 是非常類似於 ODBC 為基礎的 MFC 資料庫類別中的資料錄欄位交換 (RFX) ( `CDatabase`， `CRecordset`)。 如果您了解 RFX，您會發現簡單易用的 DFX。

A`CDaoFieldExchange`物件提供內容資訊所需適用於 DAO 資料錄欄位交換進行。 `CDaoFieldExchange` 物件支援多個作業，包括繫結參數和欄位資料成員，以及目前的資料錄的欄位上設定各種旗標。 DFX 作業將會在資料錄集類別的型別所定義的資料成員**enum** **FieldType**在`CDaoFieldExchange`。 可能**FieldType**的值為：

- `CDaoFieldExchange::outputColumn` 欄位資料成員。

- `CDaoFieldExchange::param` 參數之資料成員。

[IsValidOperation](#isvalidoperation)撰寫您自己的自訂 DFX 常式提供成員函式。 您將使用[SetFieldType](#setfieldtype)經常在您[CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)函式。 如需 DFX 全域函式的詳細資訊，請參閱[記錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。 撰寫您自己的資料類型的自訂 DFX 常式的相關資訊，請參閱[技術的附註 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDaoFieldExchange`

## <a name="requirements"></a>需求

**標頭：** afxdao.h

##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation

如果您撰寫您自己的 DFX 函式，呼叫`IsValidOperation`在您的函式，以判斷是否可以在特定欄位資料成員型別上執行目前的操作開頭 (`CDaoFieldExchange::outputColumn`或`CDaoFieldExchange::param`)。

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>傳回值

如果目前的作業是適用於更新之欄位的類型為非零。

### <a name="remarks"></a>備註

某些 DFX 機制所執行的作業僅適用於其中一種可能的欄位類型。 請遵循現有的 DFX 函式的模型。

如需有關如何撰寫自訂 DFX 常式的詳細資訊，請參閱[技術的附註 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)。

##  <a name="m_noperation"></a>  CDaoFieldExchange::m_nOperation

識別要在上執行的作業[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)欄位 exchange 物件相關聯的物件。

### <a name="remarks"></a>備註

`CDaoFieldExchange`物件可提供許多不同的資料錄集的 DFX 作業的內容。

> [!NOTE]
>  描述於下面的 「 MarkForAddNew 」 和 「 SetFieldNull 作業 PSEUDONULL 值是用來標記欄位為 Null 的值。 DAO 資料錄欄位交換 (DFX) 機制會使用此值來決定哪些欄位有已明確標記為 Null。 PSEUDONULL 不需要[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)並[COleCurrency](../../mfc/reference/colecurrency-class.md)欄位。

可能值`m_nOperation`是：

|運算|描述|
|---------------|-----------------|
|`AddToParameterList`|建置**參數**子句的 SQL 陳述式。|
|`AddToSelectList`|建置**選取**子句的 SQL 陳述式。|
|`BindField`|在您的應用程式中的記憶體位置，繫結資料庫中的欄位。|
|`BindParam`|設定資料錄集的查詢參數值。|
|`Fixup`|設定欄位的 Null 狀態。|
|`AllocCache`|會配置用來檢查有"dirty"欄位中資料錄集的快取。|
|`StoreField`|將目前的記錄儲存至快取中。|
|`LoadField`|還原資料錄集的快取的資料成員變數。|
|`FreeCache`|釋放用來檢查有"dirty"欄位中資料錄集的快取。|
|`SetFieldNull`|欄位的狀態設定為 Null，而且 PSEUDONULL 的值。|
|`MarkForAddNew`|標記的欄位 「 中途 」 如果不 PSEUDONULL。|
|`MarkForEdit`|標示的欄位"dirty"，如果不符合快取。|
|`SetDirtyField`|設定欄位值標示為 「 中途 」。|
|`DumpField`|傾印欄位的內容 （只用於偵錯）。|
|`MaxDFXOperation`|用於輸入檢查。|

##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs

包含的指標[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)相關聯的物件`CDaoFieldExchange`物件。

### <a name="remarks"></a>備註

##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType

呼叫`SetFieldType`在您`CDaoRecordset`類別的`DoFieldExchange`覆寫。

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>參數

*nFieldType*<br/>
值為**enum FieldType**中宣告`CDaoFieldExchange`，它可以是下列其中一項：

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>備註

一般來說，ClassWizard 會為您撰寫這個呼叫。 如果您撰寫您自己的函式，並使用精靈來撰寫您`DoFieldExchange`函式中，新增您自己的函式，欄位對應外面的呼叫。 如果您不使用精靈，將不會有的欄位對應。 呼叫之前呼叫 DFX 函式，一個用於您的類別，每個欄位資料成員，並且識別欄位類型為`CDaoFieldExchange::outputColumn`。

如果您將參數化資料錄集類別，您應該新增 （外部欄位對應的） 的所有參數的資料成員的 DFX 呼叫，並在呼叫這些呼叫`SetFieldType`。 將值傳遞`CDaoFieldExchange::param`。 (相反地，您可以使用[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)並設定其參數值。)

一般情況下，每個群組的欄位資料成員或參數的資料成員相關聯的 DFX 函式呼叫的前面必須有呼叫`SetFieldType`。 *NFieldType*每個參數`SetFieldType`呼叫識別遵循 DFX 函式呼叫所代表的資料成員的型別`SetFieldType`呼叫。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)
