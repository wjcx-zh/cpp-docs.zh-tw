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
ms.openlocfilehash: 265fca7288ca2aa760fb1faffa94f9d74896a975
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214096"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver 類別

實作 OLE Automation 的用戶端。

## <a name="syntax"></a>語法

```
class COleDispatchDriver
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleDispatchDriver：： COleDispatchDriver](#coledispatchdriver)|建構 `COleDispatchDriver` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleDispatchDriver：： AttachDispatch](#attachdispatch)|將 `IDispatch` 連接附加至 `COleDispatchDriver` 物件。|
|[COleDispatchDriver：： Createdispatch 範例](#createdispatch)|建立 `IDispatch` 連接，並將其附加至 `COleDispatchDriver` 物件。|
|[COleDispatchDriver：:D etachDispatch](#detachdispatch)|卸離 `IDispatch` 連接，而不釋放它。|
|[COleDispatchDriver：： GetProperty](#getproperty)|取得 automation 屬性。|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Helper，用於呼叫 automation 方法。|
|[COleDispatchDriver：： ReleaseDispatch](#releasedispatch)|釋放 `IDispatch` 連接。|
|[COleDispatchDriver：： SetProperty](#setproperty)|設定 automation 屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[COleDispatchDriver：： operator =](#operator_eq)|將來源值複製到 `COleDispatchDriver` 物件中。|
|[COleDispatchDriver：： operator LPDISPATCH](#operator_lpdispatch)|存取基礎 `IDispatch` 指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleDispatchDriver：： m_bAutoRelease](#m_bautorelease)|指定是否要在執行 `IDispatch` 期間 `ReleaseDispatch` 或物件損毀時釋放。|
|[COleDispatchDriver：： m_lpDispatch](#m_lpdispatch)|表示 `IDispatch` 附加至這個之介面的指標 `COleDispatchDriver` 。|

## <a name="remarks"></a>備註

`COleDispatchDriver`沒有基類。

OLE 分派介面可讓您存取物件的方法和屬性。 `COleDispatchDriver`附加、卸離、建立和發行類型之分派連接的成員函式 `IDispatch` 。 其他成員函式會使用可變引數清單來簡化呼叫 `IDispatch::Invoke` 。

這個類別可以直接使用，但通常僅供 [加入類別] wizard 所建立的類別使用。 當您藉由匯入類型程式庫來建立新的 c + + 類別時，新的類別會衍生自 `COleDispatchDriver` 。

如需有關使用的詳細資訊 `COleDispatchDriver` ，請參閱下列文章：

- [自動化用戶端](../../mfc/automation-clients.md)

- [Automation 伺服器](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`COleDispatchDriver`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver：： AttachDispatch

呼叫 `AttachDispatch` 成員函式可將 `IDispatch` 指標附加至 `COleDispatchDriver` 物件。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

```cpp
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

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver：： COleDispatchDriver

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
參考現有的 `COleDispatchDriver` 物件。

### <a name="remarks"></a>備註

表單 `COleDispatchDriver` （ `LPDISPATCH lpDispatch` ， **BOOL** `bAutoRelease`  =  **TRUE**）會連接[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)介面。

Form `COleDispatchDriver` （ **`const`** `COleDispatchDriver` &  `dispatchSrc` ）會複製現有的 `COleDispatchDriver` 物件，並遞增參考計數。

Form `COleDispatchDriver` （） `COleDispatchDriver` 會建立物件，但不會連接 `IDispatch` 介面。 `COleDispatchDriver`在沒有引數的情況下使用（）之前，您應該 `IDispatch` 使用[COleDispatchDriver：： createdispatch 範例](#createdispatch)或[COleDispatchDriver：： AttachDispatch](#attachdispatch)將連接到它。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](#createdispatch)的範例。

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver：： Createdispatch 範例

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

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver：:D etachDispatch

卸離 `IDispatch` 這個物件的目前連接。

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>傳回值

先前附加之 OLE 物件的指標 `IDispatch` 。

### <a name="remarks"></a>備註

`IDispatch`未釋放。

如需 LPDISPATCH 類型的詳細資訊，請參閱在 Windows SDK 中[執行 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver：： GetProperty

取得*dwDispID*所指定的物件屬性。

```cpp
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要抓取的屬性。

*vtProp*<br/>
指定要抓取的屬性。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](#invokehelper)的＜備註＞一節。

*pvProp*<br/>
將接收屬性值的變數位址。 它必須符合*vtProp*所指定的類型。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver：： InvokeHelper

在*wFlags*所指定的內容中，呼叫*dwDispID*所指定的物件方法或屬性。

```cpp
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
描述呼叫之內容的旗標 `IDispatch::Invoke` 。 . 如需可能值的清單，請參閱 Windows SDK 中[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)中的*wFlags*參數。

*vtRet*<br/>
指定傳回值的類型。 如需了解可能的值，請參閱＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須符合*vtRet*所指定的類型。

*pbParamInfo*<br/>
以 null 結束的位元組字串指標，指定*pbParamInfo*之後的參數類型。

*...*<br/>
參數的變數清單，屬於*pbParamInfo*中指定的類型。

### <a name="remarks"></a>備註

*PbParamInfo*參數會指定傳遞至方法或屬性的參數類型。 引數的變數清單會以 **...** 語法宣告代表。

*VtRet*引數的可能值取自 VARENUM 列舉。 可能值如下所示：

|符號|傳回類型|
|------------|-----------------|
|VT_EMPTY|**`void`**|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|**CY**|
|VT_DATE|**日期**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**型**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

*PbParamInfo*引數是以空格分隔的**VTS_** 常數清單。 其中的一或多個值 (以空格分隔，而非逗號) 會指定函式的參數清單。 可能的值會列在 [EVENT_CUSTOM](event-maps.md#event_custom) 巨集中。

此函式會將參數轉換為 VARIANTARG 值，然後再叫用 [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 方法。 若呼叫 `Invoke` 失敗，此函式會擲回例外狀況。 如果 DISP_E_EXCEPTION 傳回的 SCODE （狀態碼） `IDispatch::Invoke` 為，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)物件，否則會擲回[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)。

如需詳細資訊，請參閱[VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant)、在 Windows SDK 中[執行 idispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)、 [IDISPATCH：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)和[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](#createdispatch)的範例。

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver：： m_bAutoRelease

若為 TRUE，則會在呼叫[ReleaseDispatch](#releasedispatch)或終結此物件時，自動釋放由[M_LPDISPATCH](#m_lpdispatch)存取的 COM 物件 `COleDispatchDriver` 。

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>備註

根據預設， `m_bAutoRelease` 在此函式中會設定為 TRUE。

如需有關釋放 COM 物件的詳細資訊，請參閱在 Windows SDK 中[執行參考計數](/windows/win32/com/implementing-reference-counting)和[IUnknown：： Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver：： m_lpDispatch

`IDispatch`附加至這個之介面的指標 `COleDispatchDriver` 。

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>備註

`m_lpDispatch`資料成員是 LPDISPATCH 類型的公用變數。

如需詳細資訊，請參閱 Windows SDK 中的[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) 。

### <a name="example"></a>範例

  請參閱[COleDispatchDriver：： AttachDispatch](#attachdispatch)的範例。

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver：： operator =

將來源值複製到 `COleDispatchDriver` 物件中。

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>參數

*dispatchSrc*<br/>
現有物件的指標 `COleDispatchDriver` 。

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver：： operator LPDISPATCH

存取物件的基礎 `IDispatch` 指標 `COleDispatchDriver` 。

```
operator LPDISPATCH();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver：： ReleaseDispatch

釋放 `IDispatch` 連接。 如需詳細資訊，請參閱[執行 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>備註

如果已針對此連接設定自動發行，則此函式會 `IDispatch::Release` 在釋放介面之前呼叫。

### <a name="example"></a>範例

  請參閱[COleDispatchDriver：： AttachDispatch](#attachdispatch)的範例。

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver：： SetProperty

設定*dwDispID*所指定的 OLE 物件屬性。

```cpp
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
*VtProp*所指定之類型的單一參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CALCDRIV:](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 ACDUAL:](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
