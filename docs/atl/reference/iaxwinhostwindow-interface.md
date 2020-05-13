---
title: IAxWinHost 視窗介面
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
ms.openlocfilehash: ebecc611660a788ce59bb11beb95bd60eacaf01b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329990"
---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHost 視窗介面

此介面提供操作控制件及其宿主物件的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
interface IAxWinHostWindow : IUnknown
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[附加控制](#attachcontrol)|將現有控制件附加到主機物件。|
|[CreateControl](#createcontrol)|創建控制項並將其附加到主機物件。|
|[建立控制Ex](#createcontrolex)|創建控制項,將其附加到主機物件,並可以選擇設定事件處理程式。|
|[查詢控制](#querycontrol)|返回指向托管控件的介面指標。|
|[設定外部排程](#setexternaldispatch)|設置外部`IDispatch`介面。|
|[設定外部 UIHandler](#setexternaluihandler)|設置外部`IDocHostUIHandlerDispatch`介面。|

## <a name="remarks"></a>備註

此介面由 ATL 的 ActiveX 控制項託管物件公開。 呼叫此介面上的方法以建立和/或將控制項附加到主機物件、從托管控件獲取介面或設置外部介面或 UI 處理程式,以便託管 Web 瀏覽器時使用。

## <a name="requirements"></a>需求

此介面的定義可作為 IDL 或C++,如下所示。

|定義類型|檔案|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (也包含在 ATLBase.h 中)|

## <a name="iaxwinhostwindowattachcontrol"></a><a name="attachcontrol"></a>IAxWinHost 視窗::附加控制

使用*hWnd*標識的視窗將現有(以前初始化)控制件附加到主機物件。

```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```

### <a name="parameters"></a>參數

*pUnkControl*<br/>
[在]指向要附加到主機`IUnknown`物件的控制埠介面的指標。

*hWnd*<br/>
[在]用於託管的視窗的句柄。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowcreatecontrol"></a><a name="createcontrol"></a>IAxWinHost 視窗:建立控制

創建控制項,初始化它,並將其託管在*hWnd*識別的視窗中。

```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```

### <a name="parameters"></a>參數

*lpTricsData*<br/>
[在]識別要建立的控制項的字串。 可以是 CLSID(必須包括大括號)、ProgID、URL 或原始 HTML(由**MSHTML**預置: 。

*hWnd*<br/>
[在]用於託管的視窗的句柄。

*pStream*<br/>
[在]包含控制程式初始化資料的流的介面指標。 可以是 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此視窗將由公開此介面的主機物件進行子分類,以便消息可以反射到控制項,其他容器功能將起作用。

呼叫此方法等效於呼叫[IAxWinHostWindow::createControlEx](#createcontrolex)。

要建立授權的 ActiveX 控制件,請參閱[IAxWinHostWindowlic::建立控制項](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

## <a name="iaxwinhostwindowcreatecontrolex"></a><a name="createcontrolex"></a>IAxWinHost 視窗:建立控制Ex

建立一個 ActiveX 控制件,初始化它,並將其託管在指定的視窗中,類似於[IAxWinHostWindow::建立控制](#createcontrol)。

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
[在]識別要建立的控制項的字串。 可以是 CLSID(必須包括大括號)、ProgID、URL 或原始 HTML(與**MSHTML**一起預置碼: 。

*hWnd*<br/>
[在]用於託管的視窗的句柄。

*pStream*<br/>
[在]包含控制程式初始化資料的流的介面指標。 可以是 NULL。

*普恩克*<br/>
[出]將接收創建控制項介面`IUnknown`的指標的位址。 可以是 NULL。

*里德建議*<br/>
[在]包含物件上傳出介面的介面標識符。 可以IID_NULL。

*龐克建議*<br/>
[在]指向要連接到`IUnknown`所指定包含物件的連接點的接收器物件的介面的`iidSink`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

與`CreateControl`方法不同`CreateControlEx`,還允許您接收指向新創建的控制項的介面指標,並設置事件接收器以接收控制項觸發的事件。

要建立授權的 ActiveX 控制件,請參閱[IAxWinHostWindowlic::建立控制項](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。

## <a name="iaxwinhostwindowquerycontrol"></a><a name="querycontrol"></a>IAxWinHost 視窗::查詢控制

返回托管控件提供的指定介面指標。

```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>參數

*riid*<br/>
[在]請求的控制項上的介面的 ID。

*ppvObject*<br/>
[出]將接收已創建控制項的指定介面的指標的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>IAxWinHost 視窗::設定外部排程

設置外部介面,可透過[IDocHostUIHandlerDispatch:get 外部](../../atl/reference/idochostuihandlerdispatch-interface.md)方法包含控制項。

```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[在]指向介面的`IDispatch`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="iaxwinhostwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>IAxWinHost 視窗::設定外部 UIHandler

呼叫此函數以設定`CAxWindow`物件的外部[IDocHostUIHandlerDispatch 介面](../../atl/reference/idochostuihandlerdispatch-interface.md)。

```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[在]指向介面的`IDocHostUIHandlerDispatch`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此函數由查詢主機網站的`IDocHostUIHandlerDispatch`介面的控制項(如Web瀏覽器控制項)使用。

## <a name="see-also"></a>另請參閱

[IAxWin 環境排程介面](../../atl/reference/iaxwinambientdispatch-interface.md)<br/>
[CAx 視窗::查詢主機](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
