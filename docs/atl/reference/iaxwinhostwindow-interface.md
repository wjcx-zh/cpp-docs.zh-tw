---
title: IAxWinHostWindow 介面
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindow
- ATLIFACE/ATL::IAxWinHostWindow
- ATLIFACE/ATL::AttachControl
- ATLIFACE/ATL::CreateControl
- ATLIFACE/ATL::CreateControlEx
- ATLIFACE/ATL::QueryControl
- ATLIFACE/ATL::SetExternalDispatch
- ATLIFACE/ATL::SetExternalUIHandler
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
ms.openlocfilehash: 4bdfdf76b48c1e9f2c06213ee25cd15a113525dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276103"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 介面

這個介面會提供方法來操作控制項和其主機物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AttachControl](#attachcontrol)|將現有的控制項附加到主機的物件。|
|[CreateControl](#createcontrol)|建立控制項，並將它附加到主機的物件。|
|[CreateControlEx](#createcontrolex)|建立控制項，將其附加到主機物件，並選擇性地設定的事件處理常式。|
|[QueryControl](#querycontrol)|傳回裝載之控制項的介面指標。|
|[SetExternalDispatch](#setexternaldispatch)|設定外部`IDispatch`介面。|
|[SetExternalUIHandler](#setexternaluihandler)|設定外部`IDocHostUIHandlerDispatch`介面。|

## <a name="remarks"></a>備註

這個介面會公開由裝載物件的 ATL 的 ActiveX 控制項。 建立及/或將控制項附加至主機的物件，從裝載控制項取得的介面，或裝載的網頁瀏覽器時，設定外部 dispinterface 或 UI 處理常式，使用此介面上呼叫的方法。

## <a name="requirements"></a>需求

此介面的定義可從 IDL 或C++，如下所示。

|定義類型|檔案|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h （也包含在 ATLBase.h）|

##  <a name="attachcontrol"></a>  IAxWinHostWindow::AttachControl

將現有的 （與先前初始化的） 的控制項附加至使用視窗所識別的主物件*hWnd*。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>參數

*pUnkControl*<br/>
[in]指標`IUnknown`要附加至主機的物件之控制項的介面。

*hWnd*<br/>
[in]要用來裝載之視窗控制代碼。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="createcontrol"></a>  IAxWinHostWindow::CreateControl

建立控制項，它初始化，並將它裝載在視窗中所識別*hWnd*。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
[in]字串，識別要建立的控制項。 可以是 （必須包含在大括號） 的 CLSID、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。

*hWnd*<br/>
[in]要用來裝載之視窗控制代碼。

*pStream*<br/>
[in]包含控制項的初始化資料的資料流介面指標。 可以是 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此視窗會公開這個介面，讓訊息可以反映至控制項和其他容器功能將可運作的主機物件的子類別化。

呼叫這個方法就相當於呼叫[IAxWinHostWindow::CreateControlEx](#createcontrolex)。

若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

##  <a name="createcontrolex"></a>  IAxWinHostWindow::CreateControlEx

建立 ActiveX 控制項，它初始化，並將它裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。

```
STDMETHOD(CreateControlEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
[in]字串，識別要建立的控制項。 可以是 （必須包含在大括號） 的 CLSID、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。

*hWnd*<br/>
[in]要用來裝載之視窗控制代碼。

*pStream*<br/>
[in]包含控制項的初始化資料的資料流介面指標。 可以是 NULL。

*ppUnk*<br/>
[out]將會收到的指標位址`IUnknown`介面建立的控制項。 可以是 NULL。

*riidAdvise*<br/>
[in]在所包含的物件上的輸出介面的介面識別項。 可以是 IID_NULL。

*punkAdvise*<br/>
[in]指標`IUnknown`連接到包含的物件所指定的連接點的接收器物件的介面`iidSink`。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

不同於`CreateControl`方法，`CreateControlEx`也可讓您接收新建立之控制項的介面指標，並設定要接收控制項所引發的事件的事件接收。

若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

##  <a name="querycontrol"></a>  IAxWinHostWindow::QueryControl

傳回所裝載的控制項提供指定的介面指標。

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
[in]所要求的控制項上的介面識別碼。

*ppvObject*<br/>
[out]將會收到建立控制項的指定的介面的指標位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="setexternaldispatch"></a>  IAxWinHostWindow::SetExternalDispatch

設定外部 dispinterface，也就是可包含的控制項，透過[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[in]指標`IDispatch`介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="setexternaluihandler"></a>  IAxWinHostWindow::SetExternalUIHandler

呼叫此函式來設定外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面`CAxWindow`物件。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[in]指標`IDocHostUIHandlerDispatch`介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

這個函數由控制項 （例如 Web 瀏覽器控制項），查詢主機的網站`IDocHostUIHandlerDispatch`介面。

## <a name="see-also"></a>另請參閱

[IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
