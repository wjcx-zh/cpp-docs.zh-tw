---
title: COleDispatchDriver 類別
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: 9d0ffba2e8b682a33dc435b0968c59844a858c72
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524933"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver 類別

實作 OLE Automation 的用戶端。

## <a name="syntax"></a>語法

```
class COleDispatchDriver
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|建構 `COleDispatchDriver` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|附加`IDispatch`連線`COleDispatchDriver`物件。|
|[Coledispatchdriver:: Createdispatch](#createdispatch)|會建立`IDispatch`連線並將它附加至`COleDispatchDriver`物件。|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|卸離`IDispatch`連線，但未釋放它。|
|[COleDispatchDriver::GetProperty](#getproperty)|取得自動化屬性。|
|[Coledispatchdriver:: Invokehelper](#invokehelper)|呼叫 automation 方法的協助程式。|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|版本`IDispatch`連接。|
|[COleDispatchDriver::SetProperty](#setproperty)|設定自動化屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleDispatchDriver::operator =](#operator_eq)|將複製到來源值`COleDispatchDriver`物件。|
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|存取基礎`IDispatch`指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|指定是否要釋放`IDispatch`期間`ReleaseDispatch`或對物件解構。|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|指出指標`IDispatch`介面附加至此`COleDispatchDriver`。|

## <a name="remarks"></a>備註

`COleDispatchDriver` 沒有基底類別。

OLE 分派介面提供存取物件的方法和屬性。 成員函式`COleDispatchDriver`附加、 卸離、 建立及發行的分派連接類型`IDispatch`。 其他成員函式會使用變數引數清單來簡化呼叫`IDispatch::Invoke`。

這個類別則可以直接使用，但它通常由只加入類別精靈所建立的類別。 當您匯入類型程式庫來建立新的 c + + 類別時，將新的類別衍生自`COleDispatchDriver`。

如需有關使用`COleDispatchDriver`，請參閱下列文章：

- [Automation 用戶端](../../mfc/automation-clients.md)

- [Automation 伺服程式](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`COleDispatchDriver`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="attachdispatch"></a>  COleDispatchDriver::AttachDispatch

呼叫 `AttachDispatch` 成員函式可將 `IDispatch` 指標附加至 `COleDispatchDriver` 物件。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
要附加至 `IDispatch` 物件的 OLE `COleDispatchDriver` 物件指標。

*bAutoRelease*<br/>
指定當這個物件移出範圍時，是否要釋放此分派。

### <a name="remarks"></a>備註

這個函式會釋放已附加至 `IDispatch` 物件的任何 `COleDispatchDriver` 指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

##  <a name="coledispatchdriver"></a>  COleDispatchDriver::COleDispatchDriver

建構 `COleDispatchDriver` 物件。

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
要附加至 `IDispatch` 物件的 OLE `COleDispatchDriver` 物件指標。

*bAutoRelease*<br/>
指定當這個物件移出範圍時，是否要釋放此分派。

*dispatchSrc*<br/>
參考到現有`COleDispatchDriver`物件。

### <a name="remarks"></a>備註

表單`COleDispatchDriver`( `LPDISPATCH lpDispatch`， **BOOL**`bAutoRelease` = **TRUE**) 連線[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)介面。

表單`COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) 會複製現有`COleDispatchDriver`物件，並遞增參考計數。

表單`COleDispatchDriver`（） 會建立`COleDispatchDriver`物件，但不會連線`IDispatch`介面。 使用之前`COleDispatchDriver`（不含引數），您應該連接`IDispatch`使用其中一個[coledispatchdriver:: Createdispatch](#createdispatch)或是[COleDispatchDriver::AttachDispatch](#attachdispatch)。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](#createdispatch)的範例。

##  <a name="createdispatch"></a>  Coledispatchdriver:: Createdispatch

建立 [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 介面物件並將它附加至 `COleDispatchDriver` 物件。

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>參數

*clsid*<br/>
要建立的 `IDispatch` 連接物件類別識別碼。

*pError*<br/>
OLE 例外狀況物件的指標，會保留因建立而產生的狀態碼。

*lpszProgID*<br/>
Automation 物件之程式設計識別項的指標，例如 "Excel.Document.5"，針對此物件會建立分派物件。

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>  COleDispatchDriver::DetachDispatch

卸離目前`IDispatch`從這個物件的連接。

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>傳回值

指向先前附加 OLE`IDispatch`物件。

### <a name="remarks"></a>備註

`IDispatch`不釋放。

如需 LPDISPATCH 類型的詳細資訊，請參閱[實作 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>  COleDispatchDriver::GetProperty

取得所指定的物件屬性*dwDispID*。

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要擷取的屬性。

*vtProp*<br/>
指定要擷取的屬性。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](#invokehelper)的＜備註＞一節。

*pvProp*<br/>
將會收到屬性值的變數位址。 它必須符合所指定的型別*vtProp*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>  Coledispatchdriver:: Invokehelper

呼叫物件方法或屬性所指定*dwDispID*，在所指定的內容中*wFlags*。

```
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
指定所要叫用的屬性或方法。

*wFlags*<br/>
描述要呼叫的內容旗標`IDispatch::Invoke`。 。 如需可能值的清單，請參閱 < *wFlags*中的參數[idispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) Windows SDK 中。

*vtRet*<br/>
指定傳回值的類型。 如需了解可能的值，請參閱＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須符合所指定的型別*vtRet*。

*pbParamInfo*<br/>
以 null 終止的字串的指定類型的下列參數的位元組指標*pbParamInfo*。

*...*<br/>
變數清單的參數，在指定的型別*pbParamInfo*。

### <a name="remarks"></a>備註

*PbParamInfo*參數會指定傳遞至方法或屬性的參數類型。 引數的變數清單會以 **...** 語法宣告代表。

可能值為*vtRet*引數取自 VARENUM 列舉型別。 可能的值如下：

|符號|傳回型別|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**DATE**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

*PbParamInfo*引數是以空格分隔的清單**VTS_** 常數。 其中的一或多個值 (以空格分隔，而非逗號) 會指定函式的參數清單。 可能的值會列在 [EVENT_CUSTOM](event-maps.md#event_custom) 巨集中。

此函式會將參數轉換為 VARIANTARG 值，然後再叫用[idispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)方法。 若呼叫 `Invoke` 失敗，此函式會擲回例外狀況。 如果所傳回的 SCODE （狀態碼）`IDispatch::Invoke`是 DISP_E_EXCEPTION，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)物件; 否則會擲回[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)。

如需詳細資訊，請參閱 < [VARIANTARG](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)，[實作 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)， [idispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)，和[結構 COM 錯誤碼的](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](#createdispatch)的範例。

##  <a name="m_bautorelease"></a>  COleDispatchDriver::m_bAutoRelease

如果為 TRUE，COM 存取的物件[m_lpDispatch](#m_lpdispatch)會由系統自動釋放當[ReleaseDispatch](#releasedispatch)稱為或當這`COleDispatchDriver`物件被終結。

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>備註

根據預設，`m_bAutoRelease`建構函式中設定為 TRUE。

如需有關釋放 COM 物件的詳細資訊，請參閱[實作參考計數](/windows/desktop/com/implementing-reference-counting)並[iunknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>  COleDispatchDriver::m_lpDispatch

將指標`IDispatch`介面附加至此`COleDispatchDriver`。

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>備註

`m_lpDispatch`資料成員是型別 LPDISPATCH 的公用變數。

如需詳細資訊，請參閱 < [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[COleDispatchDriver::AttachDispatch](#attachdispatch)。

##  <a name="operator_eq"></a>  COleDispatchDriver::operator =

將複製到來源值`COleDispatchDriver`物件。

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>參數

*dispatchSrc*<br/>
指向現有的`COleDispatchDriver`物件。

##  <a name="operator_lpdispatch"></a>  COleDispatchDriver::operator LPDISPATCH

存取基礎`IDispatch`指標`COleDispatchDriver`物件。

```
operator LPDISPATCH();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>  COleDispatchDriver::ReleaseDispatch

版本`IDispatch`連接。 如需詳細資訊，請參閱[實作 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>備註

如果此連線已設定自動發行，此函數會呼叫`IDispatch::Release`之前釋放介面。

### <a name="example"></a>範例

  範例，請參閱[COleDispatchDriver::AttachDispatch](#attachdispatch)。

##  <a name="setproperty"></a>  COleDispatchDriver::SetProperty

設定所指定之 OLE 物件屬性*dwDispID*。

```
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要設定的屬性。

*vtProp*<br/>
指定要設定的屬性類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](#invokehelper)的＜備註＞一節。

*...*<br/>
所指定之類型的單一參數*vtProp*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CALCDRIV](../../visual-cpp-samples.md)<br/>
[MFC 範例 ACDUAL](../../visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
