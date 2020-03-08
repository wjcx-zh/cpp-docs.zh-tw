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
ms.openlocfilehash: 0d5991dcbf79d1c2415594636a09908586d1dc2f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864718"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 類別

這個類別會提供方法來操作裝載 ActiveX 控制項的視窗，也支援裝載授權的 ActiveX 控制項。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>參數

*TBase*<br/>
`CAxWindowT` 從中衍生的類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|建構 `CAxWindow2T` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T：： Create](#create)|建立主機視窗。|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|建立授權的 ActiveX 控制項、將它初始化、將它裝載于指定的視窗，以及從控制項抓取介面指標（或指標）。|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|可抓取視窗類別名稱的靜態方法。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAxWindow2T：： operator =](#operator_eq)|將 HWND 指派給現有的 `CAxWindow2T` 物件。|

## <a name="remarks"></a>備註

`CAxWindow2T` 提供方法來操作裝載 ActiveX 控制項的視窗。 `CAxWindow2T` 也支援裝載授權的 ActiveX 控制項。 裝載是由 " **AtlAxWinLic80**" 所提供，它是由 `CAxWindow2T`所包裝。

類別 `CAxWindow2` 會實作為 `CAxWindow2T` 類別的特製化。 此特製化宣告為：

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` 成員記載于[CAxWindow](../../atl/reference/caxwindow-class.md)之下。

如需使用此類別成員的範例，請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>需求

**標頭：** atlwin.h。h

##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

建構 `CAxWindow2T` 物件。

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的控制碼。

##  <a name="create"></a>CAxWindow2T：： Create

建立主機視窗。

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

`CAxWindow2T::Create` 會呼叫[CWindow：： Create](../../atl/reference/cwindow-class.md#create) ，並將 LPCTSTR *lpstrWndClass*參數設定為提供控制項裝載（`AtlAxWinLic80`）的視窗類別。

如需參數和傳回值的說明，請參閱 `CWindow::Create`。

**注意**如果將0當做*MenuOrID*參數的值使用，則必須將其指定為0u （預設值），以避免編譯器錯誤。

### <a name="example"></a>範例

如需使用 `CAxWindow2T::Create`的範例，請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

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

如需其餘參數和傳回值的描述，請參閱[CAxWindow：： CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) 。

### <a name="example"></a>範例

如需使用 `CAxWindow2T::CreateControlLic`的範例，請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

建立授權的 ActiveX 控制項、將它初始化、將它裝載于指定的視窗，以及從控制項抓取介面指標（或指標）。

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

如需其餘參數和傳回值的描述，請參閱[CAxWindow：： CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) 。

### <a name="example"></a>範例

如需使用 `CAxWindow2T::CreateControlLicEx`的範例，請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

抓取視窗類別的名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

字串的指標，其中包含可裝載已授權和 nonlicensed 之 ActiveX 控制項的視窗類別名稱（`AtlAxWinLic80`）。

##  <a name="operator_eq"></a>CAxWindow2T：： operator =

將 HWND 指派給現有的 `CAxWindow2T` 物件。

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的控制碼。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[控制項內含專案常見問題](../../atl/atl-control-containment-faq.md)
