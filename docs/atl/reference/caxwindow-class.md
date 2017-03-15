---
title: "CAxWindow 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxWindowT
- CAxWindow
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 24
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
ms.openlocfilehash: 202c68fa4044a7c7a6c47c52b8095c5e7227b56d
ms.lasthandoff: 02/24/2017

---
# <a name="caxwindow-class"></a>CAxWindow 類別
這個類別提供方法來操作裝載 ActiveX 控制項的視窗。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAxWindow : public CWindow
```  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AttachControl](#attachcontrol)|附加至現有的 ActiveX 控制項`CAxWindow`物件。|  
|[CAxWindow](#caxwindow)|建構 `CAxWindow` 物件。|  
|[CreateControl](#createcontrol)|建立 ActiveX 控制項、 將它初始化，以及裝載在`CAxWindow`視窗。|  
|[CreateControlEx](#createcontrolex)|建立 ActiveX 控制項，並從控制項擷取介面指標 （或指標）。|  
|[GetWndClassName](#getwndclassname)|（靜態）擷取的預先定義的類別名稱`CAxWindow`物件。|  
|[QueryControl](#querycontrol)|擷取**IUnknown**裝載 ActiveX 控制項。|  
|[QueryHost](#queryhost)|擷取**IUnknown**指標`CAxWindow`物件。|  
|[SetExternalDispatch](#setexternaldispatch)|設定所使用的外部分派介面`CAxWindow`物件。|  
|[SetExternalUIHandler](#setexternaluihandler)|設定外部**IDocHostUIHandler**所使用的介面`CAxWindow`物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](#operator_eq)|指派**HWND**至現有**CAxWindow**物件。|  
  
## <a name="remarks"></a>備註  
 這個類別提供方法來操作視窗裝載 ActiveX 控制項。 裝載由 「 **AtlAxWin80"**，這會由包裝`CAxWindow`。  
  
 類別`CAxWindow`實作為的特製化`CAxWindowT`類別。 此特製化會宣告為︰  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 如果您需要變更基底類別，您可以使用`CAxWindowT`，並指定新的基底類別做為樣板引數。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-nameattachcontrola--caxwindowattachcontrol"></a><a name="attachcontrol"></a>CAxWindow::AttachControl  
 如果已經不存在，並將指定的控制項附加至主機，請建立新的主機物件。  
  
```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```  
  
### <a name="parameters"></a>參數  
 `pControl`  
 [in]指標**IUnknown**的控制項。  
  
 `ppUnkContainer`  
 [out]指標**IUnknown**的主機 ( **AxWin**物件)。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 要附加的控制項物件必須正確地初始化之前，先呼叫`AttachControl`。  
  
##  <a name="a-namecaxwindowa--caxwindowcaxwindow"></a><a name="caxwindow"></a>CAxWindow::CAxWindow  
 建構`CAxWindow`物件使用現有的視窗物件控制代碼。  
  
```
CAxWindow(HWND hWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 現有的視窗物件的控制代碼。  
  
##  <a name="a-namecreatecontrola--caxwindowcreatecontrol"></a><a name="createcontrol"></a>CAxWindow::CreateControl  
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
 `lpszName`  
 若要建立控制項的字串指標。 格式必須如下的其中一個︰  
  
-   ProgID，例如 「 MSCAL。Calendar.7 」  
  
-   例如，"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID  
  
-   例如，"http://www.microsoft.com"的 URL  
  
-   例如，主動式文件的參考 「 file://\\\Documents\MyDoc.doc 」  
  
-   例如 HTML 片段 」 MSHTML:\<HTML >\<主體 > 這是一行文字\</Y >\</HTML > 」  
  
    > [!NOTE]
    >  「 MSHTML: 「 前面必須加上 HTML 片段，讓它會指定為 MSHTML 資料流。 在 Windows Mobile 平台支援只 ProgID 和 CLSID。 Windows CE 內嵌平台，Windows Mobile 支援 CE IE 支援以外所有型別包括 ProgID CLSID、 URL、 參考中的文件和 HTML 的片段。  
  
 `pStream`  
 [in]用來初始化控制項的屬性資料流的指標。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]將會收到的指標位址**IUnknown**的容器。 可以是**NULL**。  
  
 `dwResID`  
 HTML 資源的資源識別碼。 會建立並使用指定的資源載入 WebBrowser 控制項。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果使用這個方法的第二個版本，建立並繫結所識別的資源至 HTML 控制項`dwResID`。  
  
 這個方法可讓您與呼叫相同的結果︰  
  
 [!code-cpp[NVC_ATL_Windowing #&42;](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]  
  
 請參閱[CAxWindow2T::CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic)建立、 初始化及管理授權的 ActiveX 控制項。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`CreateControl`。  
  
##  <a name="a-namecreatecontrolexa--caxwindowcreatecontrolex"></a><a name="createcontrolex"></a>CAxWindow::CreateControlEx  
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
 `lpszName`  
 若要建立控制項的字串指標。 格式必須如下的其中一個︰  
  
-   ProgID，例如 「 MSCAL。Calendar.7 」  
  
-   例如，"{8E27C92B-1264-101C-8A2F-040224009C02}"CLSID  
  
-   例如，"http://www.microsoft.com"的 URL  
  
-   例如，主動式文件的參考 「 file://\\\Documents\MyDoc.doc 」  
  
-   例如 HTML 片段 」 MSHTML:\<HTML >\<主體 > 這是一行文字\</Y >\</HTML > 」  
  
    > [!NOTE]
    >  「 MSHTML: 「 前面必須加上 HTML 片段，讓它會指定為 MSHTML 資料流。 在 Windows Mobile 平台支援只 ProgID 和 CLSID。 Windows CE 內嵌平台，Windows Mobile 支援 CE IE 支援以外所有型別包括 ProgID CLSID、 URL、 參考中的文件和 HTML 的片段。  
  
 `pStream`  
 [in]用來初始化控制項的屬性資料流的指標。 可以是**NULL**。  
  
 `ppUnkContainer`  
 [out]將會收到的指標位址**IUnknown**的容器。 可以是**NULL**。  
  
 `ppUnkControl`  
 [out]將會收到的指標位址**IUnknown**的控制項。 可以是**NULL**。  
  
 `iidSink`  
 [in]所包含的物件上的輸出介面的介面識別項。 可以是**IID_NULL**。  
  
 *punkSink*  
 [in]指標**IUnknown**介面連線到所指定的包含物件的連接點的接收器物件`iidSink`。  
  
 `dwResID`  
 [in]HTML 資源的資源識別碼。 會建立並使用指定的資源載入 WebBrowser 控制項。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 這個方法很類似[CAxWindow::CreateControl](#createcontrol)，但不同於該方法中，`CreateControlEx`也可讓您接收新建立的控制項的介面指標，並將事件接收器設定為接收控制項引發的事件。  
  
 請參閱[CAxWindow2T::CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex)建立、 初始化及管理授權的 ActiveX 控制項。  
  
### <a name="example"></a>範例  
 請參閱[裝載 ActiveX 控制項使用 ATL 類別](../../atl/hosting-activex-controls-using-atl-axhost.md)如需使用範例`CreateControlEx`。  
  
##  <a name="a-namegetwndclassnamea--caxwindowgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow::GetWndClassName  
 擷取的視窗類別名稱。  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>傳回值  
 包含可以裝載要在未經授權的 ActiveX 控制項的視窗類別名稱的字串指標。  
  
##  <a name="a-nameoperatoreqa--caxwindowoperator-"></a><a name="operator_eq"></a>CAxWindow::operator =  
 指派`HWND`至現有`CAxWindow`物件。  
  
```
CAxWindow<TBase>& operator=(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 現有的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回目前 `CAxWindow` 物件的參考。  
  
##  <a name="a-namequerycontrola--caxwindowquerycontrol"></a><a name="querycontrol"></a>CAxWindow::QueryControl  
 擷取指定裝載控制項的介面。  
  
```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]指定控制項的介面的 IID。  
  
 `ppUnk`  
 [out]控制項的介面指標。 這個方法的範本版本，在沒有參考識別碼需要，只要傳遞的型別的介面相關聯的 uuid。  
  
 `Q`  
 [in]查詢的介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namequeryhosta--caxwindowqueryhost"></a><a name="queryhost"></a>CAxWindow::QueryHost  
 傳回指定的主機的介面。  
  
```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]指定控制項的介面的 IID。  
  
 `ppUnk`  
 [out]主機上的介面指標。 這個方法的範本版本，在沒有參考識別碼需要，只要傳遞的型別的介面相關聯的 uuid。  
  
 `Q`  
 [in]查詢的介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 主機的介面可讓您存取視窗裝載程式碼所實作的基礎功能**AxWin**。  
  
##  <a name="a-namesetexternaldispatcha--caxwindowsetexternaldispatch"></a><a name="setexternaldispatch"></a>CAxWindow::SetExternalDispatch  
 設定外部分派介面`CAxWindow`物件。  
  
```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```  
  
### <a name="parameters"></a>參數  
 `pDisp`  
 [in]指標`IDispatch`介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namesetexternaluihandlera--caxwindowsetexternaluihandler"></a><a name="setexternaluihandler"></a>CAxWindow::SetExternalUIHandler  
 設定外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)介面`CAxWindow`物件。  
  
```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```  
  
### <a name="parameters"></a>參數  
 *pUIHandler*  
 [in]指標**IDocHostUIHandlerDispatch**介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 外部`IDocHostUIHandlerDispatch`介面由控制項所使用查詢的主機網站`IDocHostUIHandlerDispatch`介面。 WebBrowser 控制項是一個這樣的控制項。  
  
## <a name="see-also"></a>另請參閱  
 [ATLCON 範例](../../visual-cpp-samples.md)   
 [CWindow 類別](../../atl/reference/cwindow-class.md)   
 [複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)


