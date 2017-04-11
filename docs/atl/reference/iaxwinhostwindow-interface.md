---
title: "IAxWinHostWindow 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindow
- No header/ATL::IAxWinHostWindow
- No header/ATL::AttachControl
- No header/ATL::CreateControl
- No header/ATL::CreateControlEx
- No header/ATL::QueryControl
- No header/ATL::SetExternalDispatch
- No header/ATL::SetExternalUIHandler
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindow interface
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: ecf88a3a6b115088dd605fff2b633bff86fb086a
ms.lasthandoff: 03/31/2017

---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 介面
這個介面會提供管理控制項和其主機物件的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
interface IAxWinHostWindow : IUnknown
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|將現有控制項附加至主應用程式物件。|  
|[CreateControl](#createcontrol)|建立控制項並將其附加到主機的物件。|  
|[CreateControlEx](#createcontrolex)|建立控制項，將其附加至主機物件，並且選擇性地設定事件處理常式。|  
|[QueryControl](#querycontrol)|傳回在裝載控制項的介面指標。|  
|[SetExternalDispatch](#setexternaldispatch)|設定外部`IDispatch`介面。|  
|[SetExternalUIHandler](#setexternaluihandler)|設定外部`IDocHostUIHandlerDispatch`介面。|  
  
## <a name="remarks"></a>備註  
 這個介面是 ATL 的 ActiveX 控制項裝載物件所公開的。 這個介面來建立及/或附加至主機物件，從裝載控制項取得的介面，或裝載的網頁瀏覽器時，設定外部的分配介面或使用的 UI 處理常式的控制項上呼叫的方法。  
  
## <a name="requirements"></a>需求  
 此介面的定義可做為 IDL 或 c + +，如下所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包含在 ATLBase.h）|  
  
##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl  
 將現有 （和先前初始化） 控制項加入至使用視窗所識別的主物件`hWnd`。  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 *pUnkControl*  
 [in]指標**IUnknown**要附加至主機的物件之控制項的介面。  
  
 `hWnd`  
 [in]要用於裝載視窗的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 建立控制項、 初始化，然後將它裝載於視窗所識別`hWnd`。  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `lpTricsData`  
 [in]識別要建立的控制項的字串。 可以是 （必須包含大括號） 的 CLSID、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 `hWnd`  
 [in]要用於裝載視窗的控制代碼。  
  
 `pStream`  
 [in]包含控制項的初始化資料的資料流的介面指標。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 此視窗會公開這個介面，以讓訊息可以反映至控制項和其他容器功能將使用的主物件的子類別化。  
  
 呼叫這個方法相當於呼叫[IAxWinHostWindow::CreateControlEx](#createcontrolex)。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。  
  
##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 建立 ActiveX 控制項、 初始化，然後將它裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 `lpTricsData`  
 [in]識別要建立的控制項的字串。 可以是 （必須包含大括號） 的 CLSID、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 `hWnd`  
 [in]要用於裝載視窗的控制代碼。  
  
 `pStream`  
 [in]包含控制項的初始化資料的資料流的介面指標。 可以是**NULL**。  
  
 `ppUnk`  
 [out]指標將會接收位址**IUnknown**建立控制項的介面。 可以是**NULL**。  
  
 *riidAdvise*  
 [in]所包含的物件上的輸出介面的介面識別碼。 可以是**IID_NULL**。  
  
 *punkAdvise*  
 [in]指標**IUnknown**介面連線到所指定的包含物件的連接點的接收器物件`iidSink`。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 不同於`CreateControl`方法，`CreateControlEx`也可讓您接收新建立的控制項的介面指標和事件接收器設定接收控制項引發的事件。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLicEx](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。  
  
##  <a name="querycontrol"></a>IAxWinHostWindow::QueryControl  
 傳回所裝載的控制項提供指定的介面指標。  
  
```
STDMETHOD(QueryControl)(
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `riid`  
 [in]所要求的控制項上的介面識別碼。  
  
 `ppvObject`  
 [out]將會收到建立控制項的指定的介面的指標位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="setexternaldispatch"></a>IAxWinHostWindow::SetExternalDispatch  
 設定外部的分配介面，可包含的控制項，透過[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。  
  
```
STDMETHOD(SetExternalDispatch)(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 [in]指標`IDispatch`介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="setexternaluihandler"></a>IAxWinHostWindow::SetExternalUIHandler  
 呼叫此函式來設定外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面`CAxWindow`物件。  
  
```
STDMETHOD(SetExternalUIHandler)(IDocHostUIHandlerDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 [in]指標**IDocHostUIHandlerDispatch**介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 此函式由查詢主機的站台的控制項 （例如 Web 瀏覽器控制項）`IDocHostUIHandlerDispatch`介面。  
  
## <a name="see-also"></a>另請參閱  
 [IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)










