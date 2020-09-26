---
title: CAxWindow2T 類別
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: e29c30e95116ad68d3498f3f8d3231a63c92c0a7
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353060"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 類別

這個類別提供的方法可操作裝載 ActiveX 控制項的視窗，也支援裝載授權的 ActiveX 控制項。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>參數

*TBase*<br/>
從中衍生的類別 `CAxWindowT` 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAxWindow2T：： CAxWindow2T](#caxwindow2t)|建構 `CAxWindow2T` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAxWindow2T：： Create](#create)|建立主視窗。|
|[CAxWindow2T：： CreateControlLic](#createcontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[CAxWindow2T：： CreateControlLicEx](#createcontrollicex)|建立授權的 ActiveX 控制項、將它初始化、將它裝載于指定的視窗中，以及抓取介面指標 (或從控制項) 的指標。|
|[CAxWindow2T：： GetWndClassName](#getwndclassname)|靜態方法，可抓取視窗類別的名稱。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CAxWindow2T：： operator =](#operator_eq)|將 HWND 指派給現有的 `CAxWindow2T` 物件。|

## <a name="remarks"></a>備註

`CAxWindow2T` 提供方法來操作裝載 ActiveX 控制項的視窗。 `CAxWindow2T` 也支援裝載授權的 ActiveX 控制項。 裝載是由由包裝的 " **AtlAxWinLic80**" 所提供 `CAxWindow2T` 。

類別 `CAxWindow2` 會實作為類別的特製化 `CAxWindow2T` 。 此特製化的宣告如下：

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` 成員記載于 [CAxWindow](../../atl/reference/caxwindow-class.md)之下。

如需使用這個類別成員的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>需求

**標頭：** atlwin。h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a> CAxWindow2T：： CAxWindow2T

建構 `CAxWindow2T` 物件。

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的控制碼。

## <a name="caxwindow2tcreate"></a><a name="create"></a> CAxWindow2T：： Create

建立主視窗。

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>備註

`CAxWindow2T::Create` 呼叫 [CWindow：： Create](../../atl/reference/cwindow-class.md#create) ，並將 LPCTSTR *lpstrWndClass* 參數設定為視窗類別，以提供控制項 (`AtlAxWinLic80`) 。

如需參數和傳回值的描述，請參閱 `CWindow::Create` 。

**注意** 如果使用0作為 *MenuOrID* 參數的值，則必須將其指定為 0u (預設值) ，以避免編譯器錯誤。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CAxWindow2T::Create` 。

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a> CAxWindow2T：： CreateControlLic

建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>參數

*bstrLicKey*<br/>
控制項的授權金鑰;如果建立 nonlicensed 控制項，則為 Null。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述，請參閱 [CAxWindow：： CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) 。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CAxWindow2T::CreateControlLic` 。

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a> CAxWindow2T：： CreateControlLicEx

建立授權的 ActiveX 控制項、將它初始化、將它裝載于指定的視窗中，以及抓取介面指標 (或從控制項) 的指標。

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>參數

*bstrLicKey*<br/>
控制項的授權金鑰;如果建立 nonlicensed 控制項，則為 Null。

### <a name="remarks"></a>備註

如需其餘參數和傳回值的描述，請參閱 [CAxWindow：： CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) 。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CAxWindow2T::CreateControlLicEx` 。

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a> CAxWindow2T：： GetWndClassName

抓取視窗類別的名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

包含視窗類別名稱的字串指標， (`AtlAxWinLic80` 可裝載授權和 Nonlicensed ActiveX 控制項的) 。

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a> CAxWindow2T：： operator =

將 HWND 指派給現有的 `CAxWindow2T` 物件。

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的控制碼。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)
