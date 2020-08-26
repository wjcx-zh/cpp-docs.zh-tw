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
ms.openlocfilehash: 44681b94e0bd1dfd757ebfa19f83074785dd95f5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833370"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 介面

此介面提供操作控制項和其主物件的方法。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[AttachControl](#attachcontrol)|將現有的控制項附加至主機物件。|
|[CreateControl](#createcontrol)|建立控制項，並將它附加至主機物件。|
|[CreateControlEx](#createcontrolex)|建立控制項、將它附加至主機物件，並選擇性地設定事件處理常式。|
|[QueryControl](#querycontrol)|傳回託管控制項的介面指標。|
|[SetExternalDispatch](#setexternaldispatch)|設定外部 `IDispatch` 介面。|
|[SetExternalUIHandler](#setexternaluihandler)|設定外部 `IDocHostUIHandlerDispatch` 介面。|

## <a name="remarks"></a>備註

這個介面是由 ATL 的 ActiveX 控制項裝載物件所公開。 呼叫這個介面上的方法，即可建立及/或將控制項附加至主機物件、從裝載的控制項取得介面，或設定外部的介面或 UI 處理常式，以便在裝載網頁瀏覽器時使用。

## <a name="requirements"></a>規格需求

此介面的定義可作為 IDL 或 c + +，如下所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|ATLIFace .idl|
|C++|ATLIFace 也會包含在 Atlbase.h 中 () |

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a> IAxWinHostWindow：： AttachControl

使用 *hWnd*所識別的視窗，將現有的 (和先前初始化的) 控制項附加至主物件。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>參數

*pUnkControl*<br/>
在要 `IUnknown` 附加至主控制項物件之控制項介面的指標。

*hWnd*<br/>
在要用於裝載的視窗控制碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a> IAxWinHostWindow：： CreateControl

建立控制項、將它初始化，然後將它裝載在 *hWnd*所識別的視窗中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
在識別要建立之控制項的字串。 可以是 CLSID (必須包含大括弧) 、ProgID、URL 或原始 HTML (前面加上 **MSHTML：**) 。

*hWnd*<br/>
在要用於裝載的視窗控制碼。

*pStream*<br/>
在資料流程的介面指標，包含控制項的初始化資料。 可以是 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此視窗會由公開此介面的主機物件進行子類別化，如此一來，就可以將訊息反映到控制項，而且其他容器功能將會運作。

呼叫這個方法相當於呼叫 [IAxWinHostWindow：： CreateControlEx](#createcontrolex)。

若要建立授權的 ActiveX 控制項，請參閱 [IAxWinHostWindowLic：： CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a> IAxWinHostWindow：： CreateControlEx

建立 ActiveX 控制項、將它初始化，然後將它裝載于指定的視窗中，類似于 [IAxWinHostWindow：： CreateControl](#createcontrol)。

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
在識別要建立之控制項的字串。 可以是 CLSID (必須包含大括弧) 、ProgID、URL 或原始 HTML (前面加上 **MSHTML：**) 。

*hWnd*<br/>
在要用於裝載的視窗控制碼。

*pStream*<br/>
在資料流程的介面指標，包含控制項的初始化資料。 可以是 NULL。

*ppUnk*<br/>
擴展將接收 `IUnknown` 所建立控制項介面之指標的位址。 可以是 NULL。

*riidAdvise*<br/>
在包含物件上之輸出介面的介面識別碼。 可以是 IID_Null。

*punkAdvise*<br/>
在要 `IUnknown` 連接到所指定之所包含物件上連接點的接收物件介面指標 `iidSink` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

與方法不同的是 `CreateControl` ， `CreateControlEx` 也可讓您接收新建立之控制項的介面指標，並設定事件接收以接收控制項所引發的事件。

若要建立授權的 ActiveX 控制項，請參閱 [IAxWinHostWindowLic：： CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a> IAxWinHostWindow：： QueryControl

傳回裝載控制項所提供的指定介面指標。

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
在所要求控制項上介面的識別碼。

*ppvObject*<br/>
擴展將接收所建立控制項之指定介面之指標的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> IAxWinHostWindow：： SetExternalDispatch

設定可透過 [IDocHostUIHandlerDispatch：： GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md) 方法供包含的控制項使用的外部介面。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在介面的指標 `IDispatch` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> IAxWinHostWindow：： SetExternalUIHandler

呼叫此函式可設定物件的外部 [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) 介面 `CAxWindow` 。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在介面的指標 `IDocHostUIHandlerDispatch` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

這個函式是由控制項 (使用，例如 Web 瀏覽器控制項) ，可查詢主機的 `IDocHostUIHandlerDispatch` 介面。

## <a name="see-also"></a>另請參閱

[IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAxWindow：： QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
