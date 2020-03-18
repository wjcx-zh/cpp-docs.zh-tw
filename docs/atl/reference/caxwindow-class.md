---
title: CAxWindow 類別
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418003"
---
# <a name="caxwindow-class"></a>CAxWindow 類別

這個類別會提供方法來操作裝載 ActiveX 控制項的視窗。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAxWindow : public CWindow
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AttachControl](#attachcontrol)|將現有的 ActiveX 控制項附加至 `CAxWindow` 物件。|
|[CAxWindow](#caxwindow)|建構 `CAxWindow` 物件。|
|[CreateControl](#createcontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載在 `CAxWindow` 視窗中。|
|[CreateControlEx](#createcontrolex)|建立 ActiveX 控制項，並從控制項抓取介面指標（或指標）。|
|[GetWndClassName](#getwndclassname)|靜止抓取 `CAxWindow` 物件的預先定義類別名稱。|
|[QueryControl](#querycontrol)|抓取主控的 ActiveX 控制項的 `IUnknown`。|
|[QueryHost](#queryhost)|抓取 `CAxWindow` 物件的 `IUnknown` 指標。|
|[SetExternalDispatch](#setexternaldispatch)|設定 `CAxWindow` 物件所使用的外部分派介面。|
|[SetExternalUIHandler](#setexternaluihandler)|設定 `CAxWindow` 物件所使用的外部 `IDocHostUIHandler` 介面。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#operator_eq)|將 HWND 指派給現有的 `CAxWindow` 物件。|

## <a name="remarks"></a>備註

這個類別會提供方法來操作裝載 ActiveX 控制項的視窗。 裝載是由 " **AtlAxWin80"** 所提供，它是由 `CAxWindow`所包裝。

類別 `CAxWindow` 會實作為 `CAxWindowT` 類別的特製化。 此特製化宣告為：

`typedef CAxWindowT<CWindow> CAxWindow;`

如果您需要變更基類，可以使用 `CAxWindowT` 並指定新的基類做為樣板引數。

## <a name="requirements"></a>需求

**標頭：** atlwin.h。h

##  <a name="attachcontrol"></a>CAxWindow::AttachControl

建立新的主機物件（如果尚未存在），並將指定的控制項附加至主機。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
在控制項之 `IUnknown` 的指標。

*ppUnkContainer*<br/>
脫銷主機之 `IUnknown` 的指標（`AxWin` 物件）。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

在呼叫 `AttachControl`之前，必須正確地初始化所附加的控制項物件。

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

使用現有的視窗物件控制碼，來構造 `CAxWindow` 物件。

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗物件的控制碼。

##  <a name="createcontrol"></a>CAxWindow：： CreateControl

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要建立控制項之字串的指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 活動文檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。 Windows Mobile 平臺僅支援 ProgID 和 CLSID。 Windows Mobile 以外的 Windows CE embedded 平臺，支援 CE IE 支援所有類型，包括 ProgID、CLSID、URL、使用中檔的參考，以及 HTML 片段。

*pStream*<br/>
在資料流程的指標，用來初始化控制項的屬性。 可以是 NULL。

*ppUnkContainer*<br/>
脫銷將接收容器 `IUnknown` 之指標的位址。 可以是 NULL。

*dwResID*<br/>
HTML 資源的資源識別碼。 隨即會使用指定的資源來建立和載入 WebBrowser 控制項。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果使用此方法的第二個版本，則會建立 HTML 控制項並將其系結至*dwResID*所識別的資源。

這個方法會提供與呼叫相同的結果：

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

請參閱[CAxWindow2T：： CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic)以建立、初始化和裝載授權的 ActiveX 控制項。

### <a name="example"></a>範例

如需使用 `CreateControl`的範例，請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx

建立 ActiveX 控制項、將它初始化，然後將它裝載於指定的視窗中。

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
要建立控制項之字串的指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 活動文檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。 Windows Mobile 平臺僅支援 ProgID 和 CLSID。 Windows Mobile 以外的 Windows CE embedded 平臺，支援 CE IE 支援所有類型，包括 ProgID、CLSID、URL、使用中檔的參考，以及 HTML 片段。

*pStream*<br/>
在資料流程的指標，用來初始化控制項的屬性。 可以是 NULL。

*ppUnkContainer*<br/>
脫銷將接收容器 `IUnknown` 之指標的位址。 可以是 NULL。

*ppUnkControl*<br/>
脫銷將接收控制項之 `IUnknown` 的指標位址。 可以是 NULL。

*iidSink*<br/>
在所包含物件上傳出介面的介面識別碼。 可以 IID_Null。

*punkSink*<br/>
在接收物件之 `IUnknown` 介面的指標，要連接到*iidSink*所指定之包含物件上的連接點。

*dwResID*<br/>
在HTML 資源的資源識別碼。 隨即會使用指定的資源來建立和載入 WebBrowser 控制項。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

這個方法類似于[CAxWindow：： CreateControl](#createcontrol)，但與該方法不同的是，`CreateControlEx` 也可以讓您接收新建立之控制項的介面指標，並設定事件接收以接收控制項所引發的事件。

請參閱[CAxWindow2T：： CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)以建立、初始化和裝載授權的 ActiveX 控制項。

### <a name="example"></a>範例

如需使用 `CreateControlEx`的範例，請參閱[使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

抓取視窗類別的名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

字串的指標，其中包含可裝載 nonlicensed ActiveX 控制項的視窗類別名稱。

##  <a name="operator_eq"></a>CAxWindow：： operator =

將 HWND 指派給現有的 `CAxWindow` 物件。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的控制碼。

### <a name="return-value"></a>傳回值

傳回目前 `CAxWindow` 物件的參考。

##  <a name="querycontrol"></a>CAxWindow::QueryControl

抓取主控控制項的指定介面。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>參數

*iid*<br/>
在指定控制項介面的 IID。

*ppUnk*<br/>
脫銷控制項介面的指標。 在這個方法的範本版本中，只要傳遞具有相關 UUID 的具類型介面，就不需要參考識別碼。

*Q*<br/>
在正在查詢的介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="queryhost"></a>CAxWindow::QueryHost

傳回指定的主機介面。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>參數

*iid*<br/>
在指定控制項介面的 IID。

*ppUnk*<br/>
脫銷主機上介面的指標。 在這個方法的範本版本中，只要傳遞具有相關 UUID 的具類型介面，就不需要參考識別碼。

*Q*<br/>
在正在查詢的介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

主機的介面可讓您存取由 `AxWin`所實作為的視窗裝載程式碼的基礎功能。

##  <a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch

設定 `CAxWindow` 物件的外部分派介面。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在`IDispatch` 介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler

設定 `CAxWindow` 物件的外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>參數

*pUIHandler*<br/>
在`IDocHostUIHandlerDispatch` 介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

外部 `IDocHostUIHandlerDispatch` 介面是供查詢主機的網站以取得 `IDocHostUIHandlerDispatch` 介面的控制項使用。 WebBrowser 控制項是一個執行此工作的控制項。

## <a name="see-also"></a>另請參閱

[ATLCON 範例](../../overview/visual-cpp-samples.md)<br/>
[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[控制項內含專案常見問題](../../atl/atl-control-containment-faq.md)
