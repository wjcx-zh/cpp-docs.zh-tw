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
ms.openlocfilehash: 6e8ebad0f99e086387bf9946323a2c1ef864f391
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523786"
---
# <a name="caxwindow-class"></a>CAxWindow 類別

這個類別提供方法，以操作裝載 ActiveX 控制項的視窗。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CAxWindow : public CWindow
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AttachControl](#attachcontrol)|附加至現有的 ActiveX 控制項`CAxWindow`物件。|
|[CAxWindow](#caxwindow)|建構 `CAxWindow` 物件。|
|[CreateControl](#createcontrol)|建立 ActiveX 控制項，它初始化，並將它在裝載`CAxWindow`視窗。|
|[CreateControlEx](#createcontrolex)|建立 ActiveX 控制項，並從控制項擷取介面指標 （或指標）。|
|[GetWndClassName](#getwndclassname)|（靜態）擷取的預先定義的類別名稱`CAxWindow`物件。|
|[QueryControl](#querycontrol)|擷取`IUnknown`裝載 ActiveX 控制項。|
|[QueryHost](#queryhost)|擷取`IUnknown`指標`CAxWindow`物件。|
|[SetExternalDispatch](#setexternaldispatch)|設定所使用的外部分派介面`CAxWindow`物件。|
|[SetExternalUIHandler](#setexternaluihandler)|設定外部`IDocHostUIHandler`所使用的介面`CAxWindow`物件。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#operator_eq)|指派至現有的 HWND`CAxWindow`物件。|

## <a name="remarks"></a>備註

這個類別提供方法，以操作視窗裝載 ActiveX 控制項。 裝載由提供 「 **AtlAxWin80"**，其中會由包裝`CAxWindow`。

類別`CAxWindow`實作為的特製化`CAxWindowT`類別。 此特製化會宣告為：

`typedef CAxWindowT<CWindow> CAxWindow;`

如果您要變更的基底類別，您可以使用`CAxWindowT`並做為範本引數中指定新的基底類別。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="attachcontrol"></a>  CAxWindow::AttachControl

如果其中一個已不存在，並將指定的控制項附加至主應用程式，請建立新的主機物件。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
[in]指標`IUnknown`的控制項。

*ppUnkContainer*<br/>
[out]指標`IUnknown`主控件的 (`AxWin`物件)。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

所附加的控制項物件必須正確地初始化之前呼叫`AttachControl`。

##  <a name="caxwindow"></a>  CAxWindow::CAxWindow

建構`CAxWindow`物件使用現有的視窗物件控制代碼。

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有的視窗物件的控制代碼。

##  <a name="createcontrol"></a>  CAxWindow::CreateControl

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
若要建立控制項的字串指標。 格式必須如下的其中一個：

- ProgID，例如"MSCAL。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID

- URL，例如 " http://www.microsoft.com "

- 這類的主動式文件的參考 「 file://\\\Documents\MyDoc.doc"

- 這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」

   > [!NOTE]
   > 「 MSHTML: 「 必須在前面的 HTML 片段，因此，它會指定為 MSHTML 資料流。 Windows Mobile 平台支援的 ProgID 和 CLSID。 Windows CE 內嵌平台，支援 CE IE 支援的 Windows Mobile 以外所有型別包括 ProgID，CLSID、 URL、 參考作用中的文件和片段的 HTML。

*pStream*<br/>
[in]用來初始化控制項的屬性資料流的指標。 可以是 NULL。

*ppUnkContainer*<br/>
[out]將會收到的指標位址`IUnknown`的容器。 可以是 NULL。

*dwResID*<br/>
HTML 資源的資源識別碼。 將建立 WebBrowser 控制項，並將其載入指定的資源。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果使用這個方法的第二個版本時，建立並繫結所識別的資源至 HTML 控制項*dwResID*。

這個方法可讓您與呼叫相同的結果：

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

請參閱[CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic)建立、 初始化和授權的 ActiveX 控制項裝載。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`CreateControl`。

##  <a name="createcontrolex"></a>  CAxWindow::CreateControlEx

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
若要建立控制項的字串指標。 格式必須如下的其中一個：

- ProgID，例如"MSCAL。Calendar.7"

- 例如"{8E27C92B-1264-101C-8A2F-040224009C02}"的 CLSID

- URL，例如 " http://www.microsoft.com "

- 這類的主動式文件的參考 「 file://\\\Documents\MyDoc.doc"

- 這類的 HTML 片段"MSHTML:\<HTML >\<主體 > 這是一行文字\</B >\</HTML > 」

   > [!NOTE]
   > 「 MSHTML: 「 必須在前面的 HTML 片段，因此，它會指定為 MSHTML 資料流。 Windows Mobile 平台支援的 ProgID 和 CLSID。 Windows CE 內嵌平台，支援 CE IE 支援的 Windows Mobile 以外所有型別包括 ProgID，CLSID、 URL、 參考作用中的文件和片段的 HTML。

*pStream*<br/>
[in]用來初始化控制項的屬性資料流的指標。 可以是 NULL。

*ppUnkContainer*<br/>
[out]將會收到的指標位址`IUnknown`的容器。 可以是 NULL。

*ppUnkControl*<br/>
[out]將會收到的指標位址`IUnknown`的控制項。 可以是 NULL。

*iidSink*<br/>
[in]在所包含的物件上的輸出介面的介面識別項。 可以是 IID_NULL。

*punkSink*<br/>
[in]指標`IUnknown`連接到包含的物件所指定的連接點的接收器物件的介面*iidSink*。

*dwResID*<br/>
[in]HTML 資源的資源識別碼。 將建立 WebBrowser 控制項，並將其載入指定的資源。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

這個方法很類似[CAxWindow::CreateControl](#createcontrol)，但不同於該方法中，`CreateControlEx`也可讓您接收新建立之控制項的介面指標，並設定要接收控制項所引發的事件的事件接收。

請參閱[CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)建立、 初始化和授權的 ActiveX 控制項裝載。

### <a name="example"></a>範例

請參閱[裝載 ActiveX 控制項使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)如需範例，會使用`CreateControlEx`。

##  <a name="getwndclassname"></a>  CAxWindow::GetWndClassName

擷取視窗類別名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

包含可以裝載要在未經授權的 ActiveX 控制項的視窗類別名稱的字串指標。

##  <a name="operator_eq"></a>  CAxWindow::operator =

指派至現有的 HWND`CAxWindow`物件。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有的視窗控制代碼。

### <a name="return-value"></a>傳回值

傳回目前 `CAxWindow` 物件的參考。

##  <a name="querycontrol"></a>  CAxWindow::QueryControl

擷取指定的介面，裝載的控制項。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]指定控制項的介面的 IID。

*ppUnk*<br/>
[out]控制項的介面指標。 在這個方法的範本版本，則不需要參考識別碼只要在傳遞具類型的介面相關聯的 uuid。

*Q*<br/>
[in]正在查詢的介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="queryhost"></a>  CAxWindow::QueryHost

傳回指定的主機的介面。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]指定控制項的介面的 IID。

*ppUnk*<br/>
[out]在主機上介面的指標。 在這個方法的範本版本，則不需要參考識別碼只要在傳遞具類型的介面相關聯的 uuid。

*Q*<br/>
[in]正在查詢的介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

主應用程式的介面可讓您存取視窗裝載程式碼所實作的基礎功能`AxWin`。

##  <a name="setexternaldispatch"></a>  CAxWindow::SetExternalDispatch

設定的外部分派介面`CAxWindow`物件。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
[in]指標`IDispatch`介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="setexternaluihandler"></a>  CAxWindow::SetExternalUIHandler

設定外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面`CAxWindow`物件。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>參數

*pUIHandler*<br/>
[in]指標`IDocHostUIHandlerDispatch`介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

外部`IDocHostUIHandlerDispatch`介面由查詢主機的網站的控制項`IDocHostUIHandlerDispatch`介面。 WebBrowser 控制項是此控制項。

## <a name="see-also"></a>另請參閱

[ATLCON 範例](../../visual-cpp-samples.md)<br/>
[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)

