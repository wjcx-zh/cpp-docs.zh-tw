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
ms.openlocfilehash: b74ecb9af2decf92f873cef8d016907b6c9474cf
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353073"
---
# <a name="caxwindow-class"></a>CAxWindow 類別

這個類別會提供方法來操作裝載 ActiveX 控制項的視窗。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
class CAxWindow : public CWindow
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|函式|說明|
|-|-|
|[AttachControl](#attachcontrol)|將現有的 ActiveX 控制項附加至 `CAxWindow` 物件。|
|[CAxWindow](#caxwindow)|建構 `CAxWindow` 物件。|
|[CreateControl](#createcontrol)|建立 ActiveX 控制項、將它初始化，然後將它裝載在 `CAxWindow` 視窗中。|
|[CreateControlEx](#createcontrolex)|建立 ActiveX 控制項，並取出介面指標 (或從控制項) 的指標。|
|[GetWndClassName](#getwndclassname)| (靜態) 會抓取物件的預先定義類別名稱 `CAxWindow` 。|
|[QueryControl](#querycontrol)|抓取 `IUnknown` 主控的 ActiveX 控制項的。|
|[QueryHost](#queryhost)|抓取 `IUnknown` 物件的指標 `CAxWindow` 。|
|[SetExternalDispatch](#setexternaldispatch)|設定物件所使用的外部分派介面 `CAxWindow` 。|
|[SetExternalUIHandler](#setexternaluihandler)|設定物件所 `IDocHostUIHandler` 使用的外部介面 `CAxWindow` 。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[運算子 =](#operator_eq)|將 HWND 指派給現有的 `CAxWindow` 物件。|

## <a name="remarks"></a>備註

這個類別會提供方法來操作裝載 ActiveX 控制項的視窗。 裝載是由由包裝的 " **AtlAxWin80"** 所提供 `CAxWindow` 。

類別 `CAxWindow` 會實作為類別的特製化 `CAxWindowT` 。 此特製化的宣告如下：

`typedef CAxWindowT<CWindow> CAxWindow;`

如果您需要變更基類，則可以使用 `CAxWindowT` ，並將新的基類指定為範本引數。

## <a name="requirements"></a>需求

**標頭：** atlwin。h

## <a name="caxwindowattachcontrol"></a><a name="attachcontrol"></a> CAxWindow：： AttachControl

建立新的主機物件（如果尚未存在），並將指定的控制項附加至主機。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>參數

*pControl*<br/>
在控制項之的指標 `IUnknown` 。

*ppUnkContainer*<br/>
擴展 `IUnknown` (物件) 之主控制項的指標 `AxWin` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

要附加的控制項物件必須在呼叫之前正確地初始化 `AttachControl` 。

## <a name="caxwindowcaxwindow"></a><a name="caxwindow"></a> CAxWindow：： CAxWindow

`CAxWindow`使用現有的視窗物件控制碼來建立物件。

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗物件的控制碼。

## <a name="caxwindowcreatecontrol"></a><a name="createcontrol"></a> CAxWindow：： CreateControl

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
要建立控制項的字串指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 現用檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。 Windows Mobile 平臺僅支援 ProgID 和 CLSID。 除了支援 CE IE 的 Windows Mobile 以外 Windows CE embedded 平臺支援所有類型，包括 ProgID、CLSID、URL、使用中檔的參考，以及 HTML 片段。

*pStream*<br/>
在用來初始化控制項屬性之資料流程的指標。 可以是 NULL。

*ppUnkContainer*<br/>
擴展將接收容器之指標的位址 `IUnknown` 。 可以是 NULL。

*dwResID*<br/>
HTML 資源的資源識別碼。 將會使用指定的資源來建立及載入 WebBrowser 控制項。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果使用此方法的第二個版本，則會建立 HTML 控制項並將其系結至 *dwResID*所識別的資源。

這個方法會提供與呼叫相同的結果：

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

請參閱 [CAxWindow2T：： CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) ，以建立、初始化和裝載授權的 ActiveX 控制項。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CreateControl` 。

## <a name="caxwindowcreatecontrolex"></a><a name="createcontrolex"></a> CAxWindow：： CreateControlEx

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
要建立控制項的字串指標。 必須以下列其中一種方式格式化：

- ProgID，例如 `"MSCAL.Calendar.7"`

- CLSID，例如 `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- URL，例如 `"<https://www.microsoft.com>"`

- 現用檔的參考，例如 `"file://\\\Documents\MyDoc.doc"`

- HTML 片段，例如 `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` 必須在 HTML 片段之前，使其被指定為 MSHTML 資料流程。 Windows Mobile 平臺僅支援 ProgID 和 CLSID。 除了支援 CE IE 的 Windows Mobile 以外 Windows CE embedded 平臺支援所有類型，包括 ProgID、CLSID、URL、使用中檔的參考，以及 HTML 片段。

*pStream*<br/>
在用來初始化控制項屬性之資料流程的指標。 可以是 NULL。

*ppUnkContainer*<br/>
擴展將接收容器之指標的位址 `IUnknown` 。 可以是 NULL。

*ppUnkControl*<br/>
擴展將接收控制項之指標的位址 `IUnknown` 。 可以是 NULL。

*iidSink*<br/>
在包含物件上之輸出介面的介面識別碼。 可以是 IID_Null。

*punkSink*<br/>
在要 `IUnknown` 連接至 *iidSink*所指定之所包含物件之連接點的接收物件介面指標。

*dwResID*<br/>
在HTML 資源的資源識別碼。 將會使用指定的資源來建立及載入 WebBrowser 控制項。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

這個方法類似于 [CAxWindow：： CreateControl](#createcontrol)，但與該方法不同的是，它 `CreateControlEx` 也可讓您接收新建立之控制項的介面指標，並設定事件接收以接收控制項所引發的事件。

請參閱 [CAxWindow2T：： CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) ，以建立、初始化和裝載授權的 ActiveX 控制項。

### <a name="example"></a>範例

如需使用的範例，請參閱 [使用 ATL AXHost 裝載 ActiveX 控制項](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CreateControlEx` 。

## <a name="caxwindowgetwndclassname"></a><a name="getwndclassname"></a> CAxWindow：： GetWndClassName

抓取視窗類別的名稱。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>傳回值

字串的指標，其中包含可裝載 nonlicensed ActiveX 控制項的視窗類別名稱。

## <a name="caxwindowoperator-"></a><a name="operator_eq"></a> CAxWindow：： operator =

將 HWND 指派給現有的 `CAxWindow` 物件。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
現有視窗的控制碼。

### <a name="return-value"></a>傳回值

傳回目前 `CAxWindow` 物件的參考。

## <a name="caxwindowquerycontrol"></a><a name="querycontrol"></a> CAxWindow：： QueryControl

抓取託管控制項的指定介面。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>參數

*Iid*<br/>
在指定控制項介面的 IID。

*ppUnk*<br/>
擴展控制項介面的指標。 在此方法的範本版本中，只要傳遞具有相關 UUID 的具型別介面，就不需要參考識別碼。

*問*<br/>
在正在查詢的介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="caxwindowqueryhost"></a><a name="queryhost"></a> CAxWindow：： QueryHost

傳回指定的主機介面。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>參數

*Iid*<br/>
在指定控制項介面的 IID。

*ppUnk*<br/>
擴展主機上介面的指標。 在此方法的範本版本中，只要傳遞具有相關 UUID 的具型別介面，就不需要參考識別碼。

*問*<br/>
在正在查詢的介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

主機的介面可讓您存取由所執行之視窗裝載程式碼的基礎功能 `AxWin` 。

## <a name="caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a> CAxWindow：： SetExternalDispatch

設定物件的外部分派介面 `CAxWindow` 。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
在介面的指標 `IDispatch` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a> CAxWindow：： SetExternalUIHandler

設定物件的外部 [IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md) 介面 `CAxWindow` 。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>參數

*pUIHandler*<br/>
在介面的指標 `IDocHostUIHandlerDispatch` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`IDocHostUIHandlerDispatch`查詢主機網站以取得介面的控制項會使用外部介面 `IDocHostUIHandlerDispatch` 。 WebBrowser 控制項是一個執行此工作的控制項。

## <a name="see-also"></a>另請參閱

[ATLCON 範例](../../overview/visual-cpp-samples.md)<br/>
[CWindow 類別](../../atl/reference/cwindow-class.md)<br/>
[複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)
