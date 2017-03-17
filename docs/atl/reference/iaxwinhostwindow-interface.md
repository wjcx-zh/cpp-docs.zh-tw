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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6e366e7e30e7b4080462fbc21c29b4ecdf0214ae
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinhostwindow-interface"></a>IAxWinHostWindow 介面
這個介面會提供方法來操作控制項和其主應用程式物件。  
  
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
|[AttachControl](#attachcontrol)|將現有的控制項附加至主應用程式物件。|  
|[CreateControl](#createcontrol)|建立控制項，並將它附加至主應用程式物件。|  
|[CreateControlEx](#createcontrolex)|建立控制項、 將它連接至主機的物件，並選擇性地設定事件處理常式。|  
|[QueryControl](#querycontrol)|裝載控制項到傳回介面指標。|  
|[SetExternalDispatch](#setexternaldispatch)|設定外部`IDispatch`介面。|  
|[SetExternalUIHandler](#setexternaluihandler)|設定外部`IDocHostUIHandlerDispatch`介面。|  
  
## <a name="remarks"></a>備註  
 這個介面是由 ATL 的 ActiveX 控制項裝載物件公開。 建立及/或將控制項連接至主機的物件，從裝載控制項取得的介面，或設定外部的分配介面或 UI 處理常式，用於裝載 Web 瀏覽器時，此介面上呼叫的方法。  
  
## <a name="requirements"></a>需求  
 此介面的定義可做為 IDL 或 c + +，如下所示。  
  
|定義類型|檔案|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h （也包含在 ATLBase.h）|  
  
##  <a name="attachcontrol"></a>IAxWinHostWindow::AttachControl  
 將現有的 （與先前初始化的） 控制項加入至使用視窗所識別的主物件`hWnd`。  
  
```
STDMETHOD(AttachControl)(IUnknown* pUnkControl, HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 *pUnkControl*  
 [in]指標**IUnknown**控制項連接至主應用程式物件的介面。  
  
 `hWnd`  
 [in]若要用來裝載視窗的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="createcontrol"></a>IAxWinHostWindow::CreateControl  
 建立控制項、 將它初始化，以及裝載於所識別的視窗`hWnd`。  
  
```
STDMETHOD(CreateControl)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream);
```  
  
### <a name="parameters"></a>參數  
 `lpTricsData`  
 [in]字串，識別要建立的控制項。 可以是的 CLSID （必須包含在大括號）、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 `hWnd`  
 [in]若要用來裝載視窗的控制代碼。  
  
 `pStream`  
 [in]包含控制項的初始化資料的資料流的介面指標。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 這個視窗會公開這個介面，以讓訊息可以反映至控制項和其他容器功能，將會使用主應用程式物件的子類別化。  
  
 呼叫這個方法就相當於呼叫[IAxWinHostWindow::CreateControlEx](#createcontrolex)。  
  
 若要建立授權的 ActiveX 控制項，請參閱[IAxWinHostWindowLic::CreateControlLic](../../atl/reference/iaxwinhostwindowlic-interface.md#createcontrollicex)。  
  
##  <a name="createcontrolex"></a>IAxWinHostWindow::CreateControlEx  
 建立 ActiveX 控制項、 將它初始化，以及裝載於指定的視窗，類似於[IAxWinHostWindow::CreateControl](#createcontrol)。  
  
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
 [in]字串，識別要建立的控制項。 可以是的 CLSID （必須包含在大括號）、 ProgID、 URL 或原始 HTML (前面加上**MSHTML:**)。  
  
 `hWnd`  
 [in]若要用來裝載視窗的控制代碼。  
  
 `pStream`  
 [in]包含控制項的初始化資料的資料流的介面指標。 可以是**NULL**。  
  
 `ppUnk`  
 [out]將會收到的指標位址**IUnknown**介面建立的控制項。 可以是**NULL**。  
  
 *riidAdvise*  
 [in]所包含的物件上的輸出介面的介面識別項。 可以是**IID_NULL**。  
  
 *punkAdvise*  
 [in]指標**IUnknown**介面連線到所指定的包含物件的連接點的接收器物件`iidSink`。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 不同於`CreateControl`方法，`CreateControlEx`也可讓您接收新建立的控制項的介面指標，並將事件接收器設定為接收控制項引發的事件。  
  
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
 設定外部的分配介面，可用於包含的控制項，透過[IDocHostUIHandlerDispatch::GetExternal](../../atl/reference/idochostuihandlerdispatch-interface.md)方法。  
  
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
 查詢主應用程式網站的控制項 （例如 Web 瀏覽器控制項） 會使用此函式`IDocHostUIHandlerDispatch`介面。  
  
## <a name="see-also"></a>另請參閱  
 [IAxWinAmbientDispatch 介面](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)   
 [AtlAxGetHost](http://msdn.microsoft.com/library/ad1f4f16-608d-4e96-8d30-04d4ca906a7b)










