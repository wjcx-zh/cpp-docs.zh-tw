---
title: COle排程驅動程式類別
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
ms.openlocfilehash: c22097c3a686857a6a5698033b7395c5d15f2570
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366074"
---
# <a name="coledispatchdriver-class"></a>COle排程驅動程式類別

實作 OLE Automation 的用戶端。

## <a name="syntax"></a>語法

```
class COleDispatchDriver
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle排程驅動程式:COle調度驅動程式](#coledispatchdriver)|建構 `COleDispatchDriver` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle調度驅動程式::附加調度](#attachdispatch)|將`IDispatch`連接附加`COleDispatchDriver`到 物件。|
|[COle 排程驅動程式:建立排程](#createdispatch)|建立`IDispatch`連接並將其附加`COleDispatchDriver`到 物件。|
|[COle排程驅動程式::Detach調度](#detachdispatch)|分離`IDispatch`連接,而不釋放它。|
|[COle調度驅動程式:取得財產](#getproperty)|獲取自動化屬性。|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|用於調用自動化方法的幫助器。|
|[COle調度驅動程式::發佈調度](#releasedispatch)|釋放`IDispatch`連接。|
|[COle排程驅動程式::設定屬性](#setproperty)|設置自動化屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COle調度驅動程式::操作員 |](#operator_eq)|複製到物件中`COleDispatchDriver`。|
|[COle調度驅動程式::操作員 LPDISPATCH](#operator_lpdispatch)|訪問基礎`IDispatch`指標。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COle排程驅動程式:m_bAutoRelease](#m_bautorelease)|指定是釋放`IDispatch`銷毀期間`ReleaseDispatch`還是物件銷毀。|
|[COle排程驅動程式:m_lpDispatch](#m_lpdispatch)|指示指向附加到此`IDispatch``COleDispatchDriver`的介面的指標。|

## <a name="remarks"></a>備註

`COleDispatchDriver`沒有基類。

OLE 調度介面提供對物件方法和屬性的訪問。 `COleDispatchDriver`附加、分離、創建和釋放類型的`IDispatch`調度連接的成員函數。 其他成員函數使用變數參數清單來簡化呼叫`IDispatch::Invoke`。

此類可以直接使用,但通常僅由添加類嚮導創建的類使用。 通過導入類型庫創建新C++類時,新類派生自`COleDispatchDriver`。

有關`COleDispatchDriver`使用的詳細資訊,請參閱以下文章:

- [Automation 用戶端](../../mfc/automation-clients.md)

- [Automation 伺服程式](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`COleDispatchDriver`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COle調度驅動程式::附加調度

呼叫 `AttachDispatch` 成員函式可將 `IDispatch` 指標附加至 `COleDispatchDriver` 物件。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

```
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
要附加至 `IDispatch` 物件的 OLE `COleDispatchDriver` 物件指標。

*B 自動釋放*<br/>
指定當這個物件移出範圍時，是否要釋放此分派。

### <a name="remarks"></a>備註

這個函式會釋放已附加至 `IDispatch` 物件的任何 `COleDispatchDriver` 指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COle排程驅動程式:COle調度驅動程式

建構 `COleDispatchDriver` 物件。

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
要附加至 `IDispatch` 物件的 OLE `COleDispatchDriver` 物件指標。

*B 自動釋放*<br/>
指定當這個物件移出範圍時，是否要釋放此分派。

*調度Src*<br/>
對現有`COleDispatchDriver`物件的引用。

### <a name="remarks"></a>備註

表單`COleDispatchDriver` `LPDISPATCH lpDispatch`( **BOOL**`bAutoRelease` = **TRUE**) 連接[IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)介面。

`COleDispatchDriver`表單 ( **const**`COleDispatchDriver`& `dispatchSrc`)`COleDispatchDriver`複製現有物件並遞增引用計數。

窗體`COleDispatchDriver`(`COleDispatchDriver`) 建立一`IDispatch`個物件, 但不連線介面。 在不使用`COleDispatchDriver`( )`IDispatch`之前,應使用[COleDispatchDriver::建立調度](#createdispatch)或[COleDispatch 驅動程式::附加調度](#attachdispatch)。 如需詳細資訊，請參閱 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](#createdispatch)的範例。

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COle 排程驅動程式:建立排程

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

*Clsid*<br/>
要建立的 `IDispatch` 連接物件類別識別碼。

*pError*<br/>
OLE 例外狀況物件的指標，會保留因建立而產生的狀態碼。

*lpszProgID*<br/>
Automation 物件之程式設計識別項的指標，例如 "Excel.Document.5"，針對此物件會建立分派物件。

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COle排程驅動程式::Detach調度

從此物件分離`IDispatch`當前連接。

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>傳回值

指向以前附加的 OLE`IDispatch`物件的指標。

### <a name="remarks"></a>備註

`IDispatch`未釋放。

有關 LPDISPATCH 類型的詳細資訊,請參閱在 Windows SDK[中 實現 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COle調度驅動程式:取得財產

獲取*dwDispID*指定的物件屬性。

```
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
標識要檢索的屬性。

*vtProp*<br/>
指定要檢索的屬性。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](#invokehelper)的＜備註＞一節。

*pvProp*<br/>
將接收屬性值的變數的位址。 它必須匹配*vtProp*指定的類型。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COle排程驅動程式::呼叫說明器

在*wFlags*指定的上下文中呼叫*dwDispID*指定的物件方法或屬性。

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
描述對`IDispatch::Invoke`的調用上下文的標誌。 . 有關可能值的清單,請參閱[IDispatch:::在](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)Windows SDK 中的調用中的*wFlags*參數。

*弗特雷特*<br/>
指定傳回值的類型。 如需了解可能的值，請參閱＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須與*vtRet*指定的類型匹配。

*pbParamInfo*<br/>
指向 null 連接端的位元串的指標,指定*pbParamInfo*之後的參數類型。

*...*<br/>
參數的變數清單,在*pbParamInfo*中指定的類型。

### <a name="remarks"></a>備註

*pbParamInfo*參數指定傳遞給方法或屬性的參數的類型。 引數的變數清單會以 **...** 語法宣告代表。

*vtRet*參數的可能值取自 VARENUM 枚舉。 可能的值如下：

|符號|傳回類型|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**長**|
|VT_R4|**浮動**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**日期**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**Bool**|
|VT_VARIANT|**變異**|
|VT_UNKNOWN|LPUNKNOWN|

*pbParamInfo*參數是**VTS_** 常量的空間分隔清單。 其中的一或多個值 (以空格分隔，而非逗號) 會指定函式的參數清單。 可能的值會列在 [EVENT_CUSTOM](event-maps.md#event_custom) 巨集中。

此函式會將參數轉換為 VARIANTARG 值，然後再叫用 [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 方法。 若呼叫 `Invoke` 失敗，此函式會擲回例外狀況。 如果返回的 SCODE(狀態代碼)DISP_E_EXCEPTION,則此函數將引發一個 COleException 物件`IDispatch::Invoke`;如果返回的 SCODE(狀態代碼)DISP_E_EXCEPTION,則此函數將引發一個[COleException](../../mfc/reference/coleexception-class.md)物件。否則,它拋出一個[COleDispatch 例外](../../mfc/reference/coledispatchexception-class.md)。

有關詳細資訊,請參閱[VARIANTARG,](/windows/win32/api/oaidl/ns-oaidl-variant)[實現 IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) [、IDispatch:::呼叫](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)與 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>範例

  請參閱 [COleDispatchDriver::CreateDispatch](#createdispatch)的範例。

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COle排程驅動程式:m_bAutoRelease

如果為 TRUE,則[當](#m_lpdispatch)調用[ReleaseDispatch](#releasedispatch)或`COleDispatchDriver`銷毀此 物件時,m_lpDispatch訪問的 COM 物件將自動釋放。

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>備註

預設情況下,`m_bAutoRelease`在建構函數中設定為 TRUE。

有關釋放 COM 物件的詳細資訊,請參閱在 Windows SDK[中 , 以參考計數](/windows/win32/com/implementing-reference-counting)與[I 未知::發布](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COle排程驅動程式:m_lpDispatch

指向附加到此`COleDispatchDriver`的`IDispatch`介面的指標。

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>備註

數據`m_lpDispatch`成員是 LPDISPATCH 類型的公共變數。

有關詳細資訊,請參閱 Windows SDK 中的[IDispatch。](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

### <a name="example"></a>範例

  請參考[COleDispatch 驅動程式的範例::附加調度](#attachdispatch)。

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COle調度驅動程式::操作員 |

複製到物件中`COleDispatchDriver`。

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>參數

*調度Src*<br/>
指向現有`COleDispatchDriver`物件的指標。

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COle調度驅動程式::操作員 LPDISPATCH

訪問`IDispatch``COleDispatchDriver`對象的基礎指標。

```
operator LPDISPATCH();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COle調度驅動程式::發佈調度

釋放`IDispatch`連接。 有關詳細資訊,請參閱實現[IDispatch 介面](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>備註

如果已為此連接設置了自動釋放,則此函數在釋放`IDispatch::Release`介面之前調用。

### <a name="example"></a>範例

  請參考[COleDispatch 驅動程式的範例::附加調度](#attachdispatch)。

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COle排程驅動程式::設定屬性

設定*dwDispID*指定的 OLE 物件屬性。

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
*vtProp*指定的類型的單個參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
