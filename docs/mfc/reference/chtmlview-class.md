---
title: "CHtmlView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlView
dev_langs:
- C++
helpviewer_keywords:
- browsers, MFC support for
- CHtmlView class
- WebBrowser control
- WebBrowser control, MFC support
ms.assetid: 904976af-73de-4aba-84ac-cfae8e2be09a
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
ms.openlocfilehash: d9d96ab02a0c49a2ece12c933f5d550a46204a39
ms.lasthandoff: 02/24/2017

---
# <a name="chtmlview-class"></a>CHtmlView 類別
在 MFC 的文件/檢視架構內容中提供 WebBrowser 控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CHtmlView : public CFormView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHtmlView::Create](#create)|建立 WebBrowser 控制項。|  
|[CHtmlView::CreateControlSite](#createcontrolsite)|可覆寫，用來建立主控表單上之控制項的控制項網站執行個體。|  
|[CHtmlView::ExecFormsCommand](#execformscommand)|使用 `IOleCommandTarget::Exec` 方法執行指定的命令。|  
|[CHtmlView::ExecWB](#execwb)|執行命令。|  
|[CHtmlView::GetAddressBar](#getaddressbar)|決定是否顯示 Internet Explorer 物件的網址列。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::GetApplication](#getapplication)|擷取代表應用程式的應用程式物件，此應用程式包含 Internet Explorer 應用程式目前的執行個體。|  
|[CHtmlView::GetBusy](#getbusy)|擷取指出下載或其他活動是否仍在進行中的值。|  
|[CHtmlView::GetContainer](#getcontainer)|擷取 WebBrowser 控制項的容器。|  
|[CHtmlView::GetFullName](#getfullname)|擷取顯示在網頁瀏覽器中的資源完整名稱，包括路徑。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::GetFullScreen](#getfullscreen)|指出 WebBrowser 控制項是在全螢幕模式或標準視窗模式中操作。|  
|[CHtmlView::GetHeight](#getheight)|擷取 Internet Explorer 主視窗的高度。|  
|[CHtmlView::GetHtmlDocument](#gethtmldocument)|擷取使用中的 HTML 文件。|  
|[CHtmlView::GetLeft](#getleft)|擷取 Internet Explorer 主視窗左邊緣的螢幕座標。|  
|[CHtmlView::GetLocationName](#getlocationname)|擷取 WebBrowser 目前顯示的資源名稱。|  
|[CHtmlView::GetLocationURL](#getlocationurl)|擷取 WebBrowser 目前顯示的資源 URL。|  
|[CHtmlView::GetMenuBar](#getmenubar)|擷取決定是否顯示功能表列的值。|  
|[CHtmlView::GetOffline](#getoffline)|擷取決定控制項是否離線的值。|  
|[CHtmlView::GetParentBrowser](#getparentbrowser)|擷取 `IDispatch` 介面的指標。 如需詳細資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。|  
|[CHtmlView::GetProperty](#getproperty)|擷取與指定物件相關聯屬性目前的值。|  
|[CHtmlView::GetReadyState](#getreadystate)|擷取網頁瀏覽器物件的就緒狀態。|  
|[CHtmlView::GetRegisterAsBrowser](#getregisterasbrowser)|指出 WebBrowser 控制項是否註冊為目標名稱解析的最上層瀏覽器進行。|  
|[CHtmlView::GetRegisterAsDropTarget](#getregisterasdroptarget)|指出 WebBrowser 控制項是否註冊為巡覽的置放目標。|  
|[CHtmlView::GetSilent](#getsilent)|指出是否可顯示所有對話方塊。|  
|[CHtmlView::GetSource](#getsource)|網頁的 HTML 原始程式碼。|  
|[CHtmlView::GetStatusBar](#getstatusbar)|指出是否顯示 Internet Explorer 狀態列。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::GetTheaterMode](#gettheatermode)|指出 WebBrowser 控制項是否為劇場模式。|  
|[CHtmlView::GetToolBar](#gettoolbar)|擷取決定是否顯示工具列的值。|  
|[CHtmlView::GetTop](#gettop)|擷取 Internet Explorer 主視窗上邊緣的螢幕座標。|  
|[CHtmlView::GetTopLevelContainer](#gettoplevelcontainer)|擷取值，指出目前的物件是否為 WebBrowser 控制項的最上層容器。|  
|[CHtmlView::GetType](#gettype)|擷取文件物件的類型名稱。|  
|[CHtmlView::GetVisible](#getvisible)|擷取指出物件為顯示或隱藏的值。|  
|[CHtmlView::GetWidth](#getwidth)|擷取 Internet Explorer 主視窗的寬度。|  
|[CHtmlView::GoBack](#goback)|在歷程清單中巡覽至上一個項目。|  
|[CHtmlView::GoForward](#goforward)|在歷程清單中巡覽至下一個項目。|  
|[CHtmlView::GoHome](#gohome)|巡覽至目前的首頁或起始頁面。|  
|[CHtmlView::GoSearch](#gosearch)|巡覽至目前的搜尋頁面。|  
|[CHtmlView::LoadFromResource](#loadfromresource)|載入 WebBrowser 控制項的資源。|  
|[CHtmlView::Navigate](#navigate)|巡覽至依 URL 找到的資源。|  
|[CHtmlView::Navigate2](#navigate2)|巡覽至依 URL 找到的資源或依完整路徑找到的檔案。|  
|[CHtmlView::OnBeforeNavigate2](#onbeforenavigate2)|在給定的 WebBrowser 中發生巡覽前呼叫 (無論是在視窗或框架項目上)。|  
|[CHtmlView::OnCommandStateChange](#oncommandstatechange)|呼叫以通知應用程式， 網頁瀏覽器命令啟用的狀態已經變更。|  
|[CHtmlView::OnDocumentComplete](#ondocumentcomplete)|呼叫以通知應用程式，文件已達到 `READYSTATE_COMPLETE` 狀態。|  
|[CHtmlView::OnDocWindowActivate](#ondocwindowactivate)|從 Internet Explorer 或 MSHTML 實作稱為[IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)，這麼做會通知 active 就地物件容器的文件視窗是啟用或停用時。|  
|[CHtmlView::OnDownloadBegin](#ondownloadbegin)|呼叫以通知應用程式，巡覽作業已經啟動。|  
|[CHtmlView::OnDownloadComplete](#ondownloadcomplete)|當巡覽作業結束、暫止或失敗時呼叫。|  
|[CHtmlView::OnEnableModeless](#onenablemodeless)|當容器建立或終結強制回應對話方塊時，呼叫以啟用或停用非強制回應對話方塊。|  
|[CHtmlView::OnFilterDataObject](#onfilterdataobject)|Internet Explorer 或 MSHTML 在主機上呼叫，允許主機替換 Internet Explorer 或 MSHTML 的資料物件。|  
|[CHtmlView::OnFrameWindowActivate](#onframewindowactivate)|從呼叫[IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)通知物件，當容器的最上層框架視窗是啟用或停用。|  
|[CHtmlView::OnFullScreen](#onfullscreen)|當 FullScreen 屬性變更時呼叫。|  
|[CHtmlView::OnGetDropTarget](#ongetdroptarget)|它正做為置放目標，讓主機提供另一個方法時，由 Internet Explorer 或 MSHTML 呼叫[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[CHtmlView::OnGetExternal](#ongetexternal)|由 Internet Explorer 或 MSHTML 呼叫，以取得主機的 `IDispatch` 介面。|  
|[CHtmlView::OnGetHostInfo](#ongethostinfo)|擷取 Internet Explorer 或 MSHTML 主機的 UI 功能。|  
|[CHtmlView::OnGetOptionKeyPath](#ongetoptionkeypath)|傳回 Internet Explorer 或 MSHTML 儲存使用者喜好設定的登錄機碼。|  
|[CHtmlView::OnHideUI](#onhideui)|當 Internet Explorer 或 MSHTML 移除其功能表與工具列時呼叫。|  
|[CHtmlView::OnMenuBar](#onmenubar)|當 MenuBar 屬性變更時呼叫。|  
|[CHtmlView::OnNavigateComplete2](#onnavigatecomplete2)|超連結的巡覽完畢後呼叫 (無論是在視窗或框架項目上)。|  
|[CHtmlView::OnNavigateError](#onnavigateerror)|巡覽至超連結失敗時，由架構呼叫。|  
|[CHtmlView::OnNewWindow2](#onnewwindow2)|當為顯示資源而建立新視窗時呼叫。|  
|[CHtmlView::OnProgressChange](#onprogresschange)|呼叫以通知應用程式，下載作業的進度已經更新。|  
|[CHtmlView::OnPropertyChange](#onpropertychange)|呼叫以通知應用程式， [PutProperty](#putproperty)方法已變更屬性的值。|  
|[CHtmlView::OnQuit](#onquit)|呼叫以通知應用程式，Internet Explorer 應用程式已經可以結束。 (僅限 Internet Explorer)|  
|[CHtmlView::OnResizeBorder](#onresizeborder)|從 Internet Explorer 或 MSHTML 實作稱為[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)，讓系統需要調整其框線空間的物件。|  
|[CHtmlView::OnShowContextMenu](#onshowcontextmenu)|當它正要顯示內容功能表時，從 Internet Explorer 或 MSHTML 呼叫。|  
|[CHtmlView::OnShowUI](#onshowui)|在 Internet Explorer 或 MSHTML 顯示其功能表與工具列之前呼叫。|  
|[CHtmlView::OnStatusBar](#onstatusbar)|當 StatusBar 屬性變更時呼叫。|  
|[CHtmlView::OnStatusTextChange](#onstatustextchange)|呼叫以通知應用程式，和 WebBrowser 控制項相關的狀態列文字已經變更。|  
|[CHtmlView::OnTheaterMode](#ontheatermode)|當 TheaterMode 屬性變更時呼叫。|  
|[CHtmlView::OnTitleChange](#ontitlechange)|呼叫以通知應用程式，WebBrowser 控制項中文件的標題是否變成可用或變更。|  
|[CHtmlView::OnToolBar](#ontoolbar)|當 ToolBar 屬性變更時呼叫。|  
|[CHtmlView::OnTranslateAccelerator](#ontranslateaccelerator)|由 Internet Explorer 或 MSHTML 呼叫時[IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)或[IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756)呼叫來處理從容器的訊息佇列的功能表快速鍵訊息。|  
|[CHtmlView::OnTranslateUrl](#ontranslateurl)|由 Internet Explorer 或 MSHTML 呼叫，讓主機有機會修改要載入的 URL。|  
|[CHtmlView::OnUpdateUI](#onupdateui)|通知主機命令狀態已變更。|  
|[CHtmlView::OnVisible](#onvisible)|當 WebBrowser 控制項的視窗必須顯示/隱藏時呼叫。|  
|[CHtmlView::PutProperty](#putproperty)|設定與指定物件相關聯屬性的值。|  
|[CHtmlView::QueryFormsCommand](#queryformscommand)|查詢使用者介面事件所產生之一或多個命令的狀態。|  
|[CHtmlView::QueryStatusWB](#querystatuswb)|查詢 WebBrowser 控制項處理中的命令狀態。|  
|[CHtmlView::Refresh](#refresh)|重新載入目前的檔案。|  
|[CHtmlView::Refresh2](#refresh2)|重新載入目前的檔案，並選擇性地防止傳送 `pragma:nocache` 標頭。|  
|[CHtmlView::SetAddressBar](#setaddressbar)|顯示或隱藏 Internet Explorer 物件的網址列。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::SetFullScreen](#setfullscreen)|設定值以決定控制項在全螢幕模式或標準視窗模式中操作。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::SetHeight](#setheight)|設定 Internet Explorer 主視窗的高度。|  
|[CHtmlView::SetLeft](#setleft)|設定 Internet Explorer 主視窗的水平位置。|  
|[CHtmlView::SetMenuBar](#setmenubar)|設定決定是否顯示控制項功能表列的值。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::SetOffline](#setoffline)|設定決定控制項是否離線的值。|  
|[CHtmlView::SetRegisterAsBrowser](#setregisterasbrowser)|設定值，指出 WebBrowser 控制項是否註冊為目標名稱解析的最上層瀏覽器。|  
|[CHtmlView::SetRegisterAsDropTarget](#setregisterasdroptarget)|設定值，指出 WebBrowser 控制項是否註冊為巡覽的置放目標。|  
|[CHtmlView::SetSilent](#setsilent)|設定決定控制項是否顯示對話方塊的值。|  
|[CHtmlView::SetStatusBar](#setstatusbar)|設定值，決定是否顯示 Internet Explorer 狀態列。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::SetTheaterMode](#settheatermode)|設定指出 WebBrowser 控制項是否為劇場模式的值。|  
|[CHtmlView::SetToolBar](#settoolbar)|設定決定是否顯示控制項工具列的值。 (忽略　WebBrowser 控制項，僅限 Internet Explorer。)|  
|[CHtmlView::SetTop](#settop)|設定 Internet Explorer 主視窗的垂直位置。|  
|[CHtmlView::SetVisible](#setvisible)|設定指出物件為顯示或隱藏的值。|  
|[CHtmlView::SetWidth](#setwidth)|設定 Internet Explorer 主視窗的寬度。|  
|[CHtmlView::Stop](#stop)|停止開啟檔案。|  
  
## <a name="remarks"></a>備註  
 WebBrowser 控制項是一個視窗，使用者在這裡可以瀏覽全球資訊網的網站，以及本機檔案系統和網路上的資料夾。 WebBrowser 控制項支援超連結和統一資源定位器 (URL) 巡覽，以及維護歷程記錄清單。  
  
## <a name="using-the-chtmlview-class-in-an-mfc-application"></a>使用 MFC 應用程式的 CHtmlView 類別  
 在標準的 MFC 架構應用程式中 (SDI 或 MDI 型)，檢視物件通常衍生自一組特製的類別。 這些類別全都衍生自 `CView`，除 `CView`提供的功能之外，還提供特製的功能。  
  
 以 `CHtmlView` 當做應用程式檢視類別的基礎，可以提供附有 WebBrowser 控制項的檢視。 這能讓應用程式變成網頁瀏覽器。 建立網頁瀏覽器型應用程式的慣用方法，是使用 [MFC 應用程式精靈]，指定 `CHtmlView` 為檢視類別。 如需實作及使用 WebBrowser 控制項在 MFC 應用程式的詳細資訊，請參閱[建立 Web 瀏覽器樣式應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)。  
  
> [!NOTE]
>  WebBrowser ActiveX 控制項 (亦即 `CHtmlView`) 僅適用於已安裝 Internet Explorer 4.0 或更新版本的 Windows NT 4.0 或更新版本中所執行的程式。  
  
 `CHtmlView`可用來存取 Web 應用程式 （和/或 HTML 文件）。 下列 `CHtmlView` 成員函式僅適用於 Internet Explorer 應用程式。 WebBrowser 控制項沿用這些函式，但作用不明顯。  
  
- [GetAddressBar](#getaddressbar)  
  
- [GetFullName](#getfullname)  
  
- [GetStatusBar](#getstatusbar)  
  
- [SetAddressBar](#setaddressbar)  
  
- [SetFullScreen](#setfullscreen)  
  
- [SetMenuBar](#setmenubar)  
  
- [SetStatusBar](#setstatusbar)  
  
- [SetToolBar](#settoolbar)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CHtmlView`  
  
## <a name="requirements"></a>需求  
 **Header:** afxhtml.h  
  
##  <a name="a-namecreatea--chtmlviewcreate"></a><a name="create"></a>CHtmlView::Create  
 呼叫此成員函式建立 WebBrowser 控制項或容器 Internet Explorer 的可執行檔。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 指向以 null 結束的字元字串的名稱的 Windows 類別。 類別名稱可以是任何名稱向[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)全域函式或**RegisterClass** Windows 函式。 如果**NULL**，會使用預先定義的預設[CFrameWnd](../../mfc/reference/cframewnd-class.md)屬性。  
  
 `lpszWindowName`  
 指向以 null 結束的字元字串，表示視窗名稱。  
  
 `dwStyle`  
 指定的視窗樣式屬性。 根據預設， **WS_VISIBLE**和**WS_CHILD**設定視窗樣式。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構指定的大小和視窗的位置。 `rectDefault`值允許指定的大小和位置的新視窗的視窗。  
  
 `pParentWnd`  
 控制項的父視窗的指標。  
  
 `nID`  
 檢視的識別碼。 根據預設，設定為**AFX_IDW_PANE_FIRST**。  
  
 `pContext`  
 指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)。 **NULL**預設。  
  
##  <a name="a-namecreatecontrolsitea--chtmlviewcreatecontrolsite"></a><a name="createcontrolsite"></a>CHtmlView::CreateControlSite  
 可覆寫，用來建立主控表單上之控制項的控制項網站執行個體。  
  
```  
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,  
    COleControlSite** ppSite,  
    UINT nID,  
    REFCLSID clsid);
```  
  
### <a name="parameters"></a>參數  
 `pContainer`  
 指標[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)包含控制項的物件。  
  
 `ppSite`  
 指標的指標[COleControlSite](../../mfc/reference/colecontrolsite-class.md)物件，提供控制項的站台。  
  
 `nID`  
 裝載控制項的識別項。  
  
 `clsid`  
 裝載控制項的 CLSID  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您可以覆寫此成員函式，以傳回您自己的控制項站台類別的執行個體。  
  
##  <a name="a-nameexecformscommanda--chtmlviewexecformscommand"></a><a name="execformscommand"></a>CHtmlView::ExecFormsCommand  
 使用 `IOleCommandTarget::Exec` 方法執行指定的命令。  
  
```  
HRESULT ExecFormsCommand(
    DWORD dwCommandID,  
    VARIANT* pVarIn,  
    VARIANT* pVarOut);
```  
  
### <a name="parameters"></a>參數  
 `dwCommandID`  
 要執行的命令。 此命令必須屬於**CMDSETID3_Forms3**群組。  
  
 *pVarIn*  
 指標**VARIANT**結構，其中包含輸入引數。 可以是**NULL**。  
  
 *pVarOut*  
 指標**VARIANT**接收命令輸出的結構。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。 如需可能值的完整清單，請參閱[IOleCommandTarget::Exec](http://msdn.microsoft.com/library/windows/desktop/ms690300)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 **ExecFormsCommand**實作的行為[IOleCommandTarget::Exec](http://msdn.microsoft.com/library/windows/desktop/ms690300)方法。  
  
##  <a name="a-nameexecwba--chtmlviewexecwb"></a><a name="execwb"></a>CHtmlView::ExecWB  
 呼叫此成員函式在 WebBrowser 或 Internet Explorer 中執行命令。  
  
```  
void ExecWB(
    OLECMDID cmdID,  
    OLECMDEXECOPT cmdexecopt,  
    VARIANT* pvaIn,  
    VARIANT* pvaOut);
```  
  
### <a name="parameters"></a>參數  
 `cmdID`  
 要執行的命令。  
  
 *cmdexecopt*  
 設定執行命令的選項。  
  
 `pvaIn`  
 Variant，用來指定命令的輸入引數。  
  
 *pvaOut*  
 Variant，用來指定命令的輸出引數。  
  
### <a name="remarks"></a>備註  
 請參閱[IWebBrowser2::ExecWB](https://msdn.microsoft.com/library/aa752117.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetaddressbara--chtmlviewgetaddressbar"></a><a name="getaddressbar"></a>CHtmlView::GetAddressBar  
 呼叫此成員函式擷取 Internet Explorer 網址列。  
  
```  
BOOL GetAddressBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果 [網址] 列是可見的。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namegetapplicationa--chtmlviewgetapplication"></a><a name="getapplication"></a>CHtmlView::GetApplication  
 呼叫此成員函式擷取包含 WebBrowser 控制項的應用程式支援的 automation 物件。  
  
```  
LPDISPATCH GetApplication() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IDispatch`主動式文件物件的介面。 如需詳細資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetbusya--chtmlviewgetbusy"></a><a name="getbusy"></a>CHtmlView::GetBusy  
 呼叫此成員函式，以判斷是否 WebBrowser 控制項可供瀏覽或下載作業。  
  
```  
BOOL GetBusy() const;  
```  
  
### <a name="return-value"></a>傳回值  
 網頁瀏覽器忙碌中; 如果為非零否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetcontainera--chtmlviewgetcontainer"></a><a name="getcontainer"></a>CHtmlView::GetContainer  
 呼叫此成員函式擷取評估的網頁瀏覽器容器的物件。  
  
```  
LPDISPATCH GetContainer() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IDispatch`主動式文件物件的介面。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetfullnamea--chtmlviewgetfullname"></a><a name="getfullname"></a>CHtmlView::GetFullName  
 呼叫此成員函式來擷取 Internet Explorer 目前顯示之檔案的完整路徑。  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含目前所顯示的檔案名稱與路徑。 如果沒有路徑和檔案名稱存在，`GetFullName`會傳回空白`CString`。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namegetfullscreena--chtmlviewgetfullscreen"></a><a name="getfullscreen"></a>CHtmlView::GetFullScreen  
 呼叫此成員函式，來判斷 WebBrowser 控制項是否在全螢幕模式或標準視窗模式中運作。  
  
```  
BOOL GetFullScreen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 WebBrowser 正以全螢幕模式; 如果為非零否則為零。  
  
### <a name="remarks"></a>備註  
 在全螢幕模式中，Internet Explorer 的主視窗最大化，並隱藏狀態列、 工具列、 功能表列和標題列。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetheighta--chtmlviewgetheight"></a><a name="getheight"></a>CHtmlView::GetHeight  
 呼叫此成員函式擷取的高度，單位為像素 WebBrowser 控制項的框架視窗。  
  
```  
long GetHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項的框架視窗高度，單位為像素。  
  
##  <a name="a-namegethtmldocumenta--chtmlviewgethtmldocument"></a><a name="gethtmldocument"></a>CHtmlView::GetHtmlDocument  
 呼叫此成員函式擷取使用中文件的 HTML 文件。  
  
```  
LPDISPATCH GetHtmlDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IDispatch`主動式文件物件的介面。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetlefta--chtmlviewgetleft"></a><a name="getleft"></a>CHtmlView::GetLeft  
 呼叫此成員函式擷取 WebBrowser 控制項內部左邊的緣和其容器左邊的緣之間的距離。  
  
```  
long GetLeft() const;  
```  
  
### <a name="return-value"></a>傳回值  
 左邊緣的距離，單位為像素。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetlocationnamea--chtmlviewgetlocationname"></a><a name="getlocationname"></a>CHtmlView::GetLocationName  
 呼叫此成員函式，以取得顯示在 WebBrowser 資源的名稱。  
  
```  
CString GetLocationName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含目前顯示在 WebBrowser 中資源的名稱。  
  
### <a name="remarks"></a>備註  
 如果資源是全球資訊網上的 HTML 網頁，則名稱會是該頁面的標題。 如果資源是資料夾或網路或本機電腦上的檔案，則名稱會是 UNC 或資料夾或檔案的完整路徑。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetlocationurla--chtmlviewgetlocationurl"></a><a name="getlocationurl"></a>CHtmlView::GetLocationURL  
 呼叫此成員函式擷取 WebBrowser 控制項顯示資源的 URL。  
  
```  
CString GetLocationURL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含目前顯示在 WebBrowser 中資源的 URL。  
  
### <a name="remarks"></a>備註  
 如果資源是資料夾或網路或本機電腦上的檔案，則名稱會是 UNC 或資料夾或檔案的完整路徑。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetmenubara--chtmlviewgetmenubar"></a><a name="getmenubar"></a>CHtmlView::GetMenuBar  
 呼叫此成員函式，以判斷是否為可見的功能表列。  
  
```  
BOOL GetMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果功能表列是可見的。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetofflinea--chtmlviewgetoffline"></a><a name="getoffline"></a>CHtmlView::GetOffline  
 呼叫此成員函式，來判斷是否離線運作的 web 瀏覽器。  
  
```  
BOOL GetOffline() const;  
```  
  
### <a name="return-value"></a>傳回值  
 網頁瀏覽器目前不在線上; 如果為非零否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetparentbrowsera--chtmlviewgetparentbrowser"></a><a name="getparentbrowser"></a>CHtmlView::GetParentBrowser  
 呼叫此成員函式擷取 WebBrowser 控制項的父物件的指標。  
  
```  
LPDISPATCH GetParentBrowser() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`IDispatch`WebBrowser 控制項的父物件的介面。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetpropertya--chtmlviewgetproperty"></a><a name="getproperty"></a>CHtmlView::GetProperty  
 呼叫此成員函式，以取得目前與控制項相關聯屬性的值。  
  
```  
BOOL GetProperty(
    LPCTSTR lpszProperty,  
    CString& strValue);  
  
COleVariant GetProperty(LPCTSTR lpszProperty);
```  
  
### <a name="parameters"></a>參數  
 `lpszProperty`  
 包含要擷取之屬性的字串指標。  
  
 `strValue`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)接收屬性的目前值的物件。  
  
### <a name="return-value"></a>傳回值  
 在第一個版本中，如果成功則為非零否則為零。 在第二個版本中， [COleVariant](../../mfc/reference/colevariant-class.md)物件。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetreadystatea--chtmlviewgetreadystate"></a><a name="getreadystate"></a>CHtmlView::GetReadyState  
 呼叫此成員函式擷取 WebBrowser 物件就緒狀態。  
  
```  
READYSTATE GetReadyState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [READYSTATE](https://msdn.microsoft.com/library/aa768362.aspx)值中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetregisterasbrowsera--chtmlviewgetregisterasbrowser"></a><a name="getregisterasbrowser"></a>CHtmlView::GetRegisterAsBrowser  
 呼叫此成員函式，以判斷是否要將 WebBrowser 物件註冊為最上層的瀏覽器為目標的名稱解析。  
  
```  
BOOL GetRegisterAsBrowser() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果瀏覽器會註冊為最上層的瀏覽器中，為非零否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetregisterasdroptargeta--chtmlviewgetregisterasdroptarget"></a><a name="getregisterasdroptarget"></a>CHtmlView::GetRegisterAsDropTarget  
 呼叫此成員函式，以判斷是否要將 WebBrowser 控制項註冊為瀏覽的置放目標。  
  
```  
BOOL GetRegisterAsDropTarget() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果瀏覽器以登錄為置放目標。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetsilenta--chtmlviewgetsilent"></a><a name="getsilent"></a>CHtmlView::GetSilent  
 呼叫此成員函式，以判斷是否可以在 WebBrowser 控制項中顯示任何對話方塊。  
  
```  
BOOL GetSilent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果無法從 WebBrowser 控制項，顯示對話方塊，非零值。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetsourcea--chtmlviewgetsource"></a><a name="getsource"></a>CHtmlView::GetSource  
 呼叫此成員函式擷取 web 網頁的 HTML 原始程式碼。  
  
```  
BOOL GetSource(CString& strRef);
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="parameters"></a>參數  
 `refString`  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)將保留原始碼。  
  
### <a name="remarks"></a>備註  
 此函式相當於在 Internet Explorer 中的 [檢視來源] 命令之處在於中傳回的原始碼`CString`。  
  
##  <a name="a-namegetstatusbara--chtmlviewgetstatusbar"></a><a name="getstatusbar"></a>CHtmlView::GetStatusBar  
 呼叫此成員函式，以判斷 WebBrowser 控制項是否顯示狀態列。  
  
```  
BOOL GetStatusBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果可以顯示狀態列。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namegettheatermodea--chtmlviewgettheatermode"></a><a name="gettheatermode"></a>CHtmlView::GetTheaterMode  
 呼叫此成員函式，以判斷網頁瀏覽器是否劇場模式。  
  
```  
BOOL GetTheaterMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 網頁瀏覽器劇場模式; 如果為非零否則為零。  
  
### <a name="remarks"></a>備註  
 劇場模式中的網頁瀏覽器時，瀏覽器的主視窗填滿整個螢幕，具有最基本的巡覽工具的工具列會出現，而狀態列上會出現在螢幕右上角。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegettoolbara--chtmlviewgettoolbar"></a><a name="gettoolbar"></a>CHtmlView::GetToolBar  
 呼叫此成員函式判斷是否可以看見工具列。  
  
```  
int GetToolBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，指出工具列是否可見。 如果工具列為可見則為非零否則為零。  
  
##  <a name="a-namegettopa--chtmlviewgettop"></a><a name="gettop"></a>CHtmlView::GetTop  
 呼叫此成員函式擷取的螢幕座標，WebBrowser 控制項的主視窗的頂端。  
  
```  
long GetTop() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此變數會接收主視窗的上邊緣的螢幕座標的位址。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegettoplevelcontainera--chtmlviewgettoplevelcontainer"></a><a name="gettoplevelcontainer"></a>CHtmlView::GetTopLevelContainer  
 呼叫此成員函式，以判斷是否 Internet Explorer WebBrowser 控制項的最上層的容器。  
  
```  
BOOL GetTopLevelContainer() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零容器是最上層的容器。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegettypea--chtmlviewgettype"></a><a name="gettype"></a>CHtmlView::GetType  
 呼叫此成員函式擷取包含使用中文件的型別名稱。  
  
```  
CString GetType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含所包含的主動式文件的型別名稱。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetvisiblea--chtmlviewgetvisible"></a><a name="getvisible"></a>CHtmlView::GetVisible  
 呼叫此成員函式來判斷所包含的物件是否為可見。  
  
```  
BOOL GetVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果物件是可見的。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegetwidtha--chtmlviewgetwidth"></a><a name="getwidth"></a>CHtmlView::GetWidth  
 擷取 Internet Explorer 主視窗的寬度。  
  
```  
long GetWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的視窗中，單位為像素寬度。  
  
##  <a name="a-namegobacka--chtmlviewgoback"></a><a name="goback"></a>CHtmlView::GoBack  
 瀏覽歷程記錄清單中的向後一個項目。  
  
```  
void GoBack();
```  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegoforwarda--chtmlviewgoforward"></a><a name="goforward"></a>CHtmlView::GoForward  
 瀏覽歷程記錄清單中的向前一個項目。  
  
```  
void GoForward();
```  
  
##  <a name="a-namegohomea--chtmlviewgohome"></a><a name="gohome"></a>CHtmlView::GoHome  
 巡覽至目前的首頁或起始頁，這是在 Internet Explorer [網際網路選項] 對話方塊或 [網際網路內容] 對話方塊中指定，從控制台存取。  
  
```  
void GoHome();
```  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namegosearcha--chtmlviewgosearch"></a><a name="gosearch"></a>CHtmlView::GoSearch  
 巡覽至目前搜尋的網頁，Internet Explorer 網際網路選項 對話方塊或 網際網路內容 對話方塊中所指定控制台中的存取。  
  
```  
void GoSearch();
```  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-nameloadfromresourcea--chtmlviewloadfromresource"></a><a name="loadfromresource"></a>CHtmlView::LoadFromResource  
 呼叫此成員函式可載入 WebBrowser 控制項中指定的資源。  
  
```  
BOOL LoadFromResource(LPCTSTR lpszResource);  
BOOL LoadFromResource(UINT nRes);
```  
  
### <a name="parameters"></a>參數  
 `lpszResource`  
 包含要載入的資源名稱的字串指標。  
  
 `nRes`  
 載入包含資源的名稱之緩衝區的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namenavigatea--chtmlviewnavigate"></a><a name="navigate"></a>CHtmlView::Navigate  
 呼叫此成員函式，以瀏覽至 URL 所識別的資源。  
  
```  
void Navigate(
    LPCTSTR URL,  
    DWORD dwFlags = 0,  
    LPCTSTR lpszTargetFrameName = NULL,  
    LPCTSTR lpszHeaders = NULL,  
    LPVOID lpvPostData = NULL,  
    DWORD dwPostDataLen = 0);
```  
  
### <a name="parameters"></a>參數  
 *URL*  
 呼叫端配置的字串，其中包含要瀏覽至 URL 或顯示檔案的完整路徑。  
  
 `dwFlags`  
 指定是否要將資源新增至歷程記錄清單、 是否要讀取或寫入快取中，以及是否要在新視窗中顯示的資源之變數的旗標。 變數可以是所定義之值的組合[BrowserNavConstants](https://msdn.microsoft.com/library/aa768360.aspx)列舉型別。  
  
 `lpszTargetFrameName`  
 包含要在其中顯示資源的框架名稱的字串指標。  
  
 `lpszHeaders`  
 指定要傳送至伺服器的 HTTP 標頭值的指標。 這些標頭會新增至預設的 Internet Explorer 標頭。 標頭可以指定這類事件的伺服器，傳遞至伺服器或狀態碼的資料類型所需的動作。 如果這個參數就會忽略*URL*不是 HTTP URL。  
  
 `lpvPostData`  
 要傳送的 HTTP POST 交易的資料指標。 例如，POST 交易用來傳送 HTML 格式所收集的資料。 如果這個參數未指定任何張貼的資料，**瀏覽**發出 HTTP GET 的交易。 如果這個參數就會忽略*URL*不是 HTTP URL。  
  
 `dwPostDataLen`  
 傳送 HTTP POST 交易資料。 例如，POST 交易用來傳送 HTML 格式所收集的資料。 如果這個參數未指定任何張貼的資料，**瀏覽**發出 HTTP GET 的交易。 如果這個參數就會忽略*URL*不是 HTTP URL。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namenavigate2a--chtmlviewnavigate2"></a><a name="navigate2"></a>CHtmlView::Navigate2  
 呼叫此成員函式，以瀏覽至 URL 所識別的資源或完整路徑所識別的檔案。  
  
```  
void Navigate2(
    LPITEMIDLIST pIDL,  
    DWORD dwFlags = 0,  
    LPCTSTR lpszTargetFrameName = NULL);

 
void Navigate2(
    LPCTSTR lpszURL,  
    DWORD dwFlags = 0,  
    LPCTSTR lpszTargetFrameName = NULL,  
    LPCTSTR lpszHeaders = NULL,  
    LPVOID lpvPostData = NULL,  
    DWORD dwPostDataLen = 0);

 
void Navigate2(
    LPCTSTR lpszURL,  
    DWORD dwFlags,  
    CByteArray& baPostedData,  
    LPCTSTR lpszTargetFrameName = NULL,  
    LPCTSTR lpszHeader = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pIDL*  
 指標[ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321)結構。  
  
 `dwFlags`  
 指定是否要將資源新增至歷程記錄清單、 是否要讀取或寫入快取中，以及是否要在新視窗中顯示的資源之變數的旗標。 變數可以是所定義之值的組合[BrowserNavConstants](https://msdn.microsoft.com/library/aa768360.aspx)列舉型別。  
  
 `lpszTargetFrameName`  
 包含要在其中顯示資源的框架名稱的字串指標。  
  
 `lpszURL`  
 包含 URL 的字串指標。  
  
 `lpvPostData`  
 傳送 HTTP POST 交易資料。 例如，POST 交易用來傳送 HTML 格式所收集的資料。 如果這個參數未指定任何張貼的資料，`Navigate2`發出 HTTP GET 的交易。 如果這個參數就會忽略*URL*並不是 HTTP 或 HTTPS URL。  
  
 `dwPostDataLen`  
 所指向的資料長度 （位元組）`lpvPostData`參數。  
  
 `lpszHeaders`  
 指定要傳送至伺服器的 HTTP 或 HTTPS 標頭值的指標。 這些標頭會新增至預設的 Internet Explorer 標頭。 標頭可以指定這類事件的伺服器，傳遞至伺服器或狀態碼的資料類型所需的動作。 如果這個參數就會忽略*URL*並不是 HTTP 或 HTTPS URL。  
  
 `baPostedData`  
 參考[CByteArray](../../mfc/reference/cbytearray-class.md)物件。  
  
### <a name="remarks"></a>備註  
 此成員函式會擴充**瀏覽**成員函式，藉由支援瀏覽上特殊資料夾，例如桌面和我的電腦 中以參數表示*pIDL*。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCHtmlHttp #&7;](../../mfc/reference/codesnippet/cpp/chtmlview-class_1.cpp)]  
  
##  <a name="a-nameonbeforenavigate2a--chtmlviewonbeforenavigate2"></a><a name="onbeforenavigate2"></a>CHtmlView::OnBeforeNavigate2  
 此成員函式會呼叫架構，會導致事件引發之前在網頁瀏覽器上進行巡覽。  
  
```  
virtual void OnBeforeNavigate2(
    LPCTSTR lpszURL,  
    DWORD nFlags,  
    LPCTSTR lpszTargetFrameName,  
    CByteArray& baPostedData,  
    LPCTSTR lpszHeaders,  
    BOOL* pbCancel);
```  
  
### <a name="parameters"></a>參數  
 `lpszURL`  
 包含要巡覽至 URL 的字串指標。  
  
 `nFlags`  
 保留供未來使用。  
  
 `lpszTargetFrameName`  
 字串，包含要在其中顯示該資源的框架名稱或**NULL**如果沒有已命名的框架的目標資源。  
  
 `baPostedData`  
 參考`CByteArray`物件，其中包含要傳送至伺服器，如果正在使用 HTTP POST 交易的資料。  
  
 `lpszHeaders`  
 包含其他 HTTP 標頭傳送到伺服器 (HTTP Url) 的字串指標。 標頭可以指定這類事件的伺服器，傳遞至伺服器或狀態碼的資料類型所需的動作。  
  
 `pbCancel`  
 取消旗標指標。 應用程式可以設定此參數，以取消瀏覽作業，或為零，以允許它繼續為非零。  
  
##  <a name="a-nameoncommandstatechangea--chtmlviewoncommandstatechange"></a><a name="oncommandstatechange"></a>CHtmlView::OnCommandStateChange  
 為了通知您的 web 瀏覽器命令啟用的狀態已變更的應用程式架構會呼叫此成員函式。  
  
```  
virtual void OnCommandStateChange(
    long nCommand,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 *nCommand*  
 其已啟用的狀態已變更的命令識別項。  
  
 `bEnable`  
 已啟用的狀態。 如果命令已啟用，或如果已停用為零，此參數為非零值。  
  
##  <a name="a-nameondocumentcompletea--chtmlviewondocumentcomplete"></a><a name="ondocumentcomplete"></a>CHtmlView::OnDocumentComplete  
 此成員函式會呼叫以通知已到達文件的應用程式架構`READYSTATE_COMPLETE`狀態。  
  
```  
virtual void OnDocumentComplete(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>參數  
 `lpszURL`  
 評估為 URL，UNC 字串的指標檔案的名稱，或巡覽至的 PIDL （項目識別項清單的指標）。  
  
### <a name="remarks"></a>備註  
 並非每個框架將會引發這個事件，但每個框架，就會引發[OnDownloadBegin](#ondownloadbegin)事件就會引發對應`OnDocumentComplete`事件。  
  
 URL 由`lpszURL`可以不同於以瀏覽至，已告訴瀏覽器，因為此 URL 是正式化和完整 URL 的 URL。 例如，如果應用程式的呼叫中指定 URL 的"www.microsoft.com"[瀏覽](#navigate)或[Navigate2](#navigate2)，傳遞的 URL`OnNavigateComplete2`會是"http://www.microsoft.com/"。 此外，如果伺服器已被瀏覽器重新導向至不同的 URL，重新導向的 URL 將會反映這裡。  
  
##  <a name="a-nameondocwindowactivatea--chtmlviewondocwindowactivate"></a><a name="ondocwindowactivate"></a>CHtmlView::OnDocWindowActivate  
 從 Internet Explorer 或 MSHTML 實作的 **IOleInPlaceActiveObject::OnDocWindowActivate**呼叫，這會在容器文件視窗啟用或停用時，通知使用中的就地物件。  
  
```  
virtual HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="parameters"></a>參數  
 `fActivate`  
 表示文件視窗的狀態。 如果這個值是零，會啟動視窗。 如果此值為零，正在停用視窗。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnDocWindowActivate`回應`OnDocWindowActivate`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameondownloadbegina--chtmlviewondownloadbegin"></a><a name="ondownloadbegin"></a>CHtmlView::OnDownloadBegin  
 開始下載文件的架構會呼叫此成員函式。  
  
```  
virtual void OnDownloadBegin();
```  
  
### <a name="remarks"></a>備註  
 不久之後引發此事件[OnBeforeNavigate2](#onbeforenavigate2)事件，除非取消瀏覽。 任何動畫或 「 忙碌中 」 表示容器需要顯示應已連線到此事件。  
  
##  <a name="a-nameondownloadcompletea--chtmlviewondownloadcomplete"></a><a name="ondownloadcomplete"></a>CHtmlView::OnDownloadComplete  
 表示巡覽作業完成之後，已暫止或失敗，架構會呼叫此成員函式。  
  
```  
virtual void OnDownloadComplete();
```  
  
##  <a name="a-nameonenablemodelessa--chtmlviewonenablemodeless"></a><a name="onenablemodeless"></a>CHtmlView::OnEnableModeless  
 Internet Explorer 或 MSHTML 顯示強制回應 UI 時呼叫。  
  
```  
virtual HRESULT OnEnableModeless(BOOL fEnable);
```  
  
### <a name="parameters"></a>參數  
 `fEnable`  
 表示主機的非強制回應對話方塊已啟用或停用。 如果此值為零，則會啟用非強制回應對話方塊。 如果此值為零，則會停用非強制回應對話方塊。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 啟用或停用非強制回應對話方塊時，容器會建立或終結強制回應對話方塊。 覆寫`OnEnableModeless`回應`EnableModeless`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonfilterdataobjecta--chtmlviewonfilterdataobject"></a><a name="onfilterdataobject"></a>CHtmlView::OnFilterDataObject  
 Internet Explorer 或 MSHTML 在主機上呼叫，允許主機替換 Internet Explorer 或 MSHTML 的資料物件。  
  
```  
virtual HRESULT OnFilterDataObject(
    LPDATAOBJECT pDataObject,  
    LPDATAOBJECT* ppDataObject);
```  
  
### <a name="parameters"></a>參數  
 `pDataObject`  
 位址[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) Internet Explorer 或 MSHTML 所提供的介面。  
  
 *ppDataObject*  
 接收的地址`IDataObject`主機所提供的介面指標。 此參數的內容應該都會初始化為**NULL**，即使方法失敗。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果取代的資料物件， **S_FALSE**未取代資料物件，或發生錯誤時，OLE 定義的錯誤程式碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnFilterDataObject`回應`FilterDataObject`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonframewindowactivatea--chtmlviewonframewindowactivate"></a><a name="onframewindowactivate"></a>CHtmlView::OnFrameWindowActivate  
 從呼叫[IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)通知物件，當容器的最上層框架視窗是啟用或停用。  
  
```  
virtual HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="parameters"></a>參數  
 `fActivate`  
 指出容器的最上層框架視窗的狀態。 如果這個值是零，會啟動視窗。 如果此值為零，正在停用視窗。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnFrameWindowActivate`回應`OnFrameWindowActivate`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonfullscreena--chtmlviewonfullscreen"></a><a name="onfullscreen"></a>CHtmlView::OnFullScreen  
 此成員函式由架構呼叫時[全螢幕](https://msdn.microsoft.com/library/aa752119.aspx)屬性已變更。  
  
```  
virtual void OnFullScreen(BOOL bFullScreen);
```  
  
### <a name="parameters"></a>參數  
 *bFullScreen*  
 Internet Explorer 以全螢幕模式; 如果為非零否則為零。  
  
##  <a name="a-nameongetdroptargeta--chtmlviewongetdroptarget"></a><a name="ongetdroptarget"></a>CHtmlView::OnGetDropTarget  
 它正做為置放目標，讓主機提供另一個方法時，由 Internet Explorer 或 MSHTML 呼叫`IDropTarget`。  
  
```  
virtual HRESULT OnGetDropTarget(
    LPDROPTARGET pDropTarget,  
    LPDROPTARGET* ppDropTarget);
```  
  
### <a name="parameters"></a>參數  
 `pDropTarget`  
 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) Internet Explorer 或 MSHTML 建議使用。  
  
 `ppDropTarget`  
 位址`IDropTarget`接收`IDropTarget`主應用程式想要提供的介面指標。  
  
### <a name="return-value"></a>傳回值  
 請參閱[IDocHostUIHandler::GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]傳回碼的清單。  
  
### <a name="remarks"></a>備註  
 覆寫`OnGetDropTarget`回應`GetDropTarget`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameongetexternala--chtmlviewongetexternal"></a><a name="ongetexternal"></a>CHtmlView::OnGetExternal  
 由 Internet Explorer 或 MSHTML 呼叫，以取得主機的 `IDispatch` 介面。  
  
```  
virtual HRESULT OnGetExternal(LPDISPATCH* lppDispatch);
```  
  
### <a name="parameters"></a>參數  
 *lppDispatch*  
 收到的位址指標`IDispatch`主應用程式的介面指標。 如果主應用程式公開 Automation 介面，它可以提供 Internet Explorer 或 MSHTML 透過此參數的參考。 此參數的內容應該都會初始化為**NULL**，即使方法失敗。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnGetExternal`回應`GetExternal`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameongethostinfoa--chtmlviewongethostinfo"></a><a name="ongethostinfo"></a>CHtmlView::OnGetHostInfo  
 擷取 Internet Explorer 或 MSHTML 主機的 UI 功能。  
  
```  
virtual HRESULT OnGetHostInfo(DOCHOSTUIINFO* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pInfo`  
 位址[DOCHOSTUIINFO](https://msdn.microsoft.com/library/aa770044.aspx)接收主機的 UI 功能的結構。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnGetHostInfo`回應`GetHostInfo`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameongetoptionkeypatha--chtmlviewongetoptionkeypath"></a><a name="ongetoptionkeypath"></a>CHtmlView::OnGetOptionKeyPath  
 呼叫此成員函式，以取得在 Internet Explorer 或 MSHTML 儲存使用者喜好設定的登錄機碼。  
  
```  
virtual HRESULT OnGetOptionKeyPath(
    LPOLESTR* pchKey,  
    DWORD dwReserved);
```  
  
### <a name="parameters"></a>參數  
 `pchKey`  
 位址`LPOLESTR`接收主機儲存它的預設選項的登錄子機碼字串。 這個子機碼將會在 hkey_current_user 機碼之下。 配置此記憶體使用[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)。 呼叫的應用程式會負責釋放這個記憶體使用[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)。 這個參數應該一律先初始化才能**NULL**，即使方法失敗。  
  
 `dwReserved`  
 保留供未來使用。 目前無法使用。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或**S_FALSE**否則。 如果**S_FALSE**，Internet Explorer 或 MSHTML 會預設為自己的使用者選項。  
  
### <a name="remarks"></a>備註  
 覆寫`OnGetOptionKeyPath`回應`GetOptionKeyPath`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonhideuia--chtmlviewonhideui"></a><a name="onhideui"></a>CHtmlView::OnHideUI  
 當 Internet Explorer 或 MSHTML 移除其功能表和工具列，架構會呼叫此成員函式。  
  
```  
virtual HRESULT OnHideUI();
```  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnHideUI`回應`HideUI`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::HideUI](https://msdn.microsoft.com/library/aa753259.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonmenubara--chtmlviewonmenubar"></a><a name="onmenubar"></a>CHtmlView::OnMenuBar  
 此成員函式由架構呼叫時[MenuBar](https://msdn.microsoft.com/library/aa752131.aspx)屬性已變更。  
  
```  
virtual void OnMenuBar(BOOL bMenuBar);
```  
  
### <a name="parameters"></a>參數  
 *bMenuBar*  
 非零，如果 Internet Explorer 的功能表列是可見的。否則為零。  
  
##  <a name="a-nameonnavigatecomplete2a--chtmlviewonnavigatecomplete2"></a><a name="onnavigatecomplete2"></a>CHtmlView::OnNavigateComplete2  
 此成員函式是由架構完成之後呼叫巡覽超連結 （在視窗或框架組的項目）。  
  
```  
virtual void OnNavigateComplete2(LPCTSTR strURL);
```  
  
### <a name="parameters"></a>參數  
 *strURL*  
 評估為 URL 的字串運算式 UNC 檔案名稱或巡覽至的 PIDL （項目識別項清單的指標）。  
  
### <a name="remarks"></a>備註  
 URL 參數可以是在沒有 URL 表示法是殼層名稱空間實體的情況下 PIDL。  
  
 請注意，URL 中包含*strURL*可以不同於以瀏覽至，已告訴瀏覽器，因為此 URL 是正式化和完整 URL 的 URL。 例如，如果應用程式的呼叫中指定 URL 的"www.microsoft.com"[瀏覽](#navigate)或[Navigate2](#navigate2)，傳遞的 URL`OnNavigateComplete2`會是"http://www.microsoft.com/"。 此外，如果伺服器已被瀏覽器重新導向至不同的 URL，重新導向的 URL 將會反映這裡。  
  
##  <a name="a-nameonnavigateerrora--chtmlviewonnavigateerror"></a><a name="onnavigateerror"></a>CHtmlView::OnNavigateError  
 巡覽至超連結失敗時，由架構呼叫。  
  
```  
virtual void OnNavigateError(
    LPCTSTR lpszURL,  
    LPCTSTR lpszFrame,  
    DWORD dwError,  
    BOOL* pbCancel);
```  
  
### <a name="parameters"></a>參數  
 `lpszURL`  
 無法瀏覽的 URL。  
  
 *lpszFrame*  
 要顯示，則為 NULL，如果沒有已命名的框架的目標資源的資源的框架名稱。  
  
 `dwError`  
 錯誤狀態碼，如果有的話。 如需可能的 HRESULT 和 HTTP 狀態碼，請參閱[NavigateError 事件狀態碼。](https://msdn.microsoft.com/library/aa768365.aspx)  
  
 `pbCancel`  
 指定是否要取消瀏覽到錯誤頁面或任何進一步的自動搜尋。 如果**TRUE** （預設值），請繼續執行瀏覽到錯誤頁面或自動搜尋; 如果**FALSE**，取消瀏覽到錯誤頁面或自動搜尋。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法以提供自訂的瀏覽錯誤處理。  
  
 如需詳細資訊，請參閱[DWebBrowserEvents2::NavigateError](https://msdn.microsoft.com/library/aa768286.aspx)  
  
##  <a name="a-nameonnewwindow2a--chtmlviewonnewwindow2"></a><a name="onnewwindow2"></a>CHtmlView::OnNewWindow2  
 顯示資源建立在新視窗開啟時，架構被呼叫此成員函式。  
  
```  
virtual void OnNewWindow2(
    LPDISPATCH* ppDisp,  
    BOOL* Cancel);
```  
  
### <a name="parameters"></a>參數  
 `ppDisp`  
 可選擇性地接收的介面指標的指標`IDispatch`WebBrowser 或 Internet Explorer 的新物件的介面指標。  
  
 `Cancel`  
 取消旗標指標。 應用程式可以設定此參數，以取消瀏覽作業，或為零，以允許它繼續為非零。  
  
### <a name="remarks"></a>備註  
 此事件之前 WebBrowser 在新視窗的建立。  
  
##  <a name="a-nameonprogresschangea--chtmlviewonprogresschange"></a><a name="onprogresschange"></a>CHtmlView::OnProgressChange  
 此成員函式會呼叫架構，以便通知應用程式已更新的下載作業的進度。  
  
```  
virtual void OnProgressChange(
    long nProgress,  
    long nProgressMax);
```  
  
### <a name="parameters"></a>參數  
 *nProgress*  
 顯示或-1 時的進度已完成的總進度數量。  
  
 *nProgressMax*  
 最大的進度值。  
  
### <a name="remarks"></a>備註  
 顯示目前下載的位元組數，或更新進度列指示器，容器就可以使用這個事件所提供的資訊。  
  
##  <a name="a-nameonpropertychangea--chtmlviewonpropertychange"></a><a name="onpropertychange"></a>CHtmlView::OnPropertyChange  
 此成員函式會呼叫以通知應用程式架構， [PutProperty](#putproperty)已變更之屬性的值。  
  
```  
virtual void OnPropertyChange(LPCTSTR lpszProperty);
```  
  
### <a name="parameters"></a>參數  
 `lpszProperty`  
 包含屬性名稱的字串指標。  
  
##  <a name="a-nameonquita--chtmlviewonquit"></a><a name="onquit"></a>CHtmlView::OnQuit  
 告知 Internet Explorer 應用程式已準備好要結束應用程式的架構會呼叫此成員函式。  
  
```  
virtual void OnQuit();
```  
  
##  <a name="a-nameonresizebordera--chtmlviewonresizeborder"></a><a name="onresizeborder"></a>CHtmlView::OnResizeBorder  
 從 Internet Explorer 或 MSHTML 實作稱為[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)，讓系統需要調整其框線空間的物件。  
  
```  
virtual HRESULT OnResizeBorder(
    LPCRECT prcBorder,  
    LPOLEINPLACEUIWINDOW pUIWindow,  
    BOOL fFrameWindow);
```  
  
### <a name="parameters"></a>參數  
 `prcBorder`  
 框線空間的新外部矩形。  
  
 `pUIWindow`  
 已變更其框線的框架或文件視窗物件的介面指標。  
  
 `fFrameWindow`  
 **TRUE**如果框架視窗呼叫[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)，否則為**FALSE**。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 覆寫`OnResizeBorder`回應`ResizeBorder`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonshowcontextmenua--chtmlviewonshowcontextmenu"></a><a name="onshowcontextmenu"></a>CHtmlView::OnShowContextMenu  
 當它正要顯示內容功能表時，從 Internet Explorer 或 MSHTML 呼叫。  
  
```  
virtual HRESULT OnShowContextMenu(
    DWORD dwID,  
    LPPOINT ppt,  
    LPUNKNOWN pcmdtReserved,  
    LPDISPATCH pdispReserved);
```  
  
### <a name="parameters"></a>參數  
 `dwID`  
 要顯示的內容功能表的識別碼。 請參閱**IDocHostUIHandler::ShowContextMenu**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
 `ppt`  
 功能表的螢幕座標。  
  
 `pcmdtReserved`  
 [IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)介面用來查詢命令的狀態，並在此物件上執行命令。  
  
 `pdispReserved`  
 在螢幕座標之物件的 IDispatch 介面。 這可讓主機區分特定物件，以提供更特定的內容。  
  
### <a name="return-value"></a>傳回值  
 請參閱[IDocHostUIHandler::ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
### <a name="remarks"></a>備註  
 覆寫`OnShowContextMenu`回應`ShowContextMenu`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonshowuia--chtmlviewonshowui"></a><a name="onshowui"></a>CHtmlView::OnShowUI  
 在 Internet Explorer 或 MSHTML 顯示其功能表與工具列之前呼叫。  
  
```  
virtual HRESULT OnShowUI(
    DWORD dwID,  
    LPOLEINPLACEACTIVEOBJECT pActiveObject,  
    LPOLECOMMANDTARGET pCommandTarget,  
    LPOLEINPLACEFRAME pFrame,  
    LPOLEINPLACEUIWINDOW pDoc);
```  
  
### <a name="parameters"></a>參數  
 `dwID`  
 保留供未來使用。  
  
 `pActiveObject`  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299)目前作用中物件的介面。  
  
 `pCommandTarget`  
 [IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)介面的物件。  
  
 `pFrame`  
 [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770)介面的物件。 這是所需的功能表和工具列。  
  
 `pDoc`  
 [IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716)物件介面。 這是所需的工具列。  
  
### <a name="return-value"></a>傳回值  
 請參閱[IDocHostUIHandler::ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
### <a name="remarks"></a>備註  
 覆寫`OnShowUI`回應`ShowUI`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonstatusbara--chtmlviewonstatusbar"></a><a name="onstatusbar"></a>CHtmlView::OnStatusBar  
 此成員函式由架構呼叫時[StatusBar](https://msdn.microsoft.com/library/aa768270.aspx)屬性已變更。  
  
```  
virtual void OnStatusBar(BOOL bStatusBar);
```  
  
### <a name="parameters"></a>參數  
 *bStatusBar*  
 如果 Internet Explorer 狀態列會顯示為非零或零，否則為。  
  
##  <a name="a-nameonstatustextchangea--chtmlviewonstatustextchange"></a><a name="onstatustextchange"></a>CHtmlView::OnStatusTextChange  
 要通知的 WebBrowser 控制項相關聯的狀態列文字已變更的應用程式架構會呼叫此成員函式。  
  
```  
virtual void OnStatusTextChange(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 包含新的狀態列文字的字串。  
  
##  <a name="a-nameontheatermodea--chtmlviewontheatermode"></a><a name="ontheatermode"></a>CHtmlView::OnTheaterMode  
 此成員函式由架構呼叫時[TheaterMode](https://msdn.microsoft.com/library/aa768273.aspx)屬性已變更。  
  
```  
virtual void OnTheaterMode(BOOL bTheaterMode);
```  
  
### <a name="parameters"></a>參數  
 *bTheaterMode*  
 如果 Internet Explorer 劇場模式，為非零否則為零。  
  
##  <a name="a-nameontitlechangea--chtmlviewontitlechange"></a><a name="ontitlechange"></a>CHtmlView::OnTitleChange  
 此成員函式會呼叫架構，以便在 WebBrowser 控制項中的文件的標題就會變成可用時，通知應用程式或變更。  
  
```  
virtual void OnTitleChange(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 新的文件標題。  
  
### <a name="remarks"></a>備註  
 Html，可能會變更標題。正在下載 HTML，而文件的 URL 會設為標題。 實際的標題 （如果有的話） 從剖析 HTML 之後，標題會變更以反映實際的標題。  
  
##  <a name="a-nameontoolbara--chtmlviewontoolbar"></a><a name="ontoolbar"></a>CHtmlView::OnToolBar  
 此成員函式由架構呼叫時[工具列](https://msdn.microsoft.com/library/aa768274.aspx)屬性已變更。  
  
```  
virtual void OnToolBar(BOOL bToolBar);
```  
  
### <a name="parameters"></a>參數  
 *bToolBar*  
 如果 Internet Explorer 工具列會顯示為非零或零，否則為。  
  
##  <a name="a-nameontranslateacceleratora--chtmlviewontranslateaccelerator"></a><a name="ontranslateaccelerator"></a>CHtmlView::OnTranslateAccelerator  
 由 Internet Explorer 或 MSHTML 呼叫時[IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)或[IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756)呼叫來處理從容器的訊息佇列的功能表快速鍵訊息。  
  
```  
virtual HRESULT OnTranslateAccelerator(
    LPMSG lpMsg,  
    const GUID* pguidCmdGroup,  
    DWORD nCmdID);
```  
  
### <a name="parameters"></a>參數  
 `lpMsg`  
 點的訊息，可能需要轉譯。  
  
 `pguidCmdGroup`  
 命令群組的識別碼。  
  
 `nCmdID`  
 命令識別項。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或**S_FALSE**否則。  
  
### <a name="remarks"></a>備註  
 覆寫`OnTranslateAccelerator`回應`TranslateAccelerator`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameontranslateurla--chtmlviewontranslateurl"></a><a name="ontranslateurl"></a>CHtmlView::OnTranslateUrl  
 由 Internet Explorer 或 MSHTML 呼叫，讓主機有機會修改要載入的 URL。  
  
```  
virtual HRESULT OnTranslateUrl(
    DWORD dwTranslate,  
    OLECHAR* pchURLIn,  
    OLECHAR** ppchURLOut);
```  
  
### <a name="parameters"></a>參數  
 `dwTranslate`  
 保留供未來使用。  
  
 `pchURLIn`  
 字串，Internet Explorer 或 MSHTML，表示要轉譯的 URL 所提供的位址。  
  
 `ppchURLOut`  
 接收轉譯的 URL 位址的字串指標的位址。 主機會配置緩衝區使用的工作記憶體配置器。 此參數的內容應該都會初始化為**NULL**，即使不會轉譯 URL 或方法失敗。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果已轉譯的 URL， **S_FALSE**如果不轉譯的 URL，或 OLE 定義的錯誤程式碼發生錯誤。  
  
### <a name="remarks"></a>備註  
 覆寫`OnTranslateUrl`回應`TranslateUrl`來自 Microsoft 的網頁瀏覽器控制項的通知。 請參閱[IDocHostUIHandler::TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="a-nameonupdateuia--chtmlviewonupdateui"></a><a name="onupdateui"></a>CHtmlView::OnUpdateUI  
 通知主機命令狀態已變更。  
  
```  
virtual HRESULT OnUpdateUI();
```  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果成功，或其他 OLE 定義的錯誤代碼。  
  
### <a name="remarks"></a>備註  
 主機應該更新工具列按鈕的狀態。 不論從傳回的值呼叫此方法`ShowUI`。 覆寫`OnUpdateUI`回應`UpdateUI`來自 Microsoft 的網頁瀏覽器控制項的通知。  
  
##  <a name="a-nameonvisiblea--chtmlviewonvisible"></a><a name="onvisible"></a>CHtmlView::OnVisible  
 時要顯示或隱藏 WebBrowser 的視窗，架構會呼叫此成員函式。  
  
```  
virtual void OnVisible(BOOL bVisible);
```  
  
### <a name="parameters"></a>參數  
 `bVisible`  
 可見的物件是否為非零或零，否則為。  
  
### <a name="remarks"></a>備註  
 這可讓物件控制主機視窗行為 Internet Explorer 視窗會以相同方式運作。  
  
##  <a name="a-nameputpropertya--chtmlviewputproperty"></a><a name="putproperty"></a>CHtmlView::PutProperty  
 呼叫此成員函式設定與指定的物件相關聯的屬性。  
  
```  
void PutProperty(
    LPCTSTR lpszProperty,  
    const VARIANT& vtValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    double dValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    long lValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    LPCTSTR lpszValue);

 
void PutProperty(
    LPCTSTR lpszPropertyName,  
    short nValue);
```  
  
### <a name="parameters"></a>參數  
 `lpszProperty`  
 字串，包含要設定的屬性。  
  
 *vtValue*  
 新屬性的值由`lpszProperty`。  
  
 *lpszPropertyName*  
 包含要設定的屬性名稱的字串指標。  
  
 *dValue*  
 屬性的新值。  
  
 `lValue`  
 屬性的新值。  
  
 `lpszValue`  
 包含屬性的新值的字串指標。  
  
 `nValue`  
 屬性的新值。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namequeryformscommanda--chtmlviewqueryformscommand"></a><a name="queryformscommand"></a>CHtmlView::QueryFormsCommand  
 查詢使用者介面事件所產生之一或多個命令的狀態。  
  
```  
HRESULT QueryFormsCommand(
    DWORD dwCommandID,  
    BOOL* pbSupported,  
    BOOL* pbEnabled,  
    BOOL* pbChecked);
```  
  
### <a name="parameters"></a>參數  
 `dwCommandID`  
 要查詢的命令識別項。  
  
 *pbSupported*  
 指標**BOOL**指定如果命令 (由`dwCommandID`) 支援。 如果為 TRUE，則被支援的命令;否則為 FALSE。  
  
 `pbEnabled`  
 指標**BOOL**指定如果命令 (由`dwCommandID`) 已啟用。 如果為 TRUE，則被支援的命令;否則為 FALSE。  
  
 *pbChecked*  
 指標**BOOL**指定如果命令 (由`dwCommandID`) 會檢查。 如果為 TRUE，則被支援的命令;否則為 FALSE。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。 如需可能值的完整清單，請參閱[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 `QueryFormsCommand`實作的行為[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)方法。  
  
##  <a name="a-namequerystatuswba--chtmlviewquerystatuswb"></a><a name="querystatuswb"></a>CHtmlView::QueryStatusWB  
 呼叫此成員函式，查詢命令狀態。  
  
```  
OLECMDF QueryStatusWB(OLECMDID cmdID) const;  
```  
  
### <a name="parameters"></a>參數  
 `cmdID`  
 [OLECMDID](http://msdn.microsoft.com/library/windows/desktop/ms691264)命令的呼叫端需要其狀態資訊的值。  
  
### <a name="return-value"></a>傳回值  
 位址[OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237)接收命令的狀態的值。  
  
### <a name="remarks"></a>備註  
 `QueryStatusWB`實作的行為[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)方法。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namerefresha--chtmlviewrefresh"></a><a name="refresh"></a>CHtmlView::Refresh  
 重新載入 URL 或 web 瀏覽器顯示的檔案。  
  
```  
void Refresh();
```  
  
### <a name="remarks"></a>備註  
 **重新整理**未包含參數來設定重新整理層級。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namerefresh2a--chtmlviewrefresh2"></a><a name="refresh2"></a>CHtmlView::Refresh2  
 重新載入 Internet Explorer 目前顯示的檔案。  
  
```  
void Refresh2(int nLevel);
```  
  
### <a name="parameters"></a>參數  
 `nLevel`  
 指定重新整理層級變數的位址。 可能的變數定義在[RefreshConstants](https://msdn.microsoft.com/library/aa768363.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 不同於[重新整理](#refresh)，`Refresh2`包含指定的重新整理層級的參數。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetaddressbara--chtmlviewsetaddressbar"></a><a name="setaddressbar"></a>CHtmlView::SetAddressBar  
 呼叫此成員函式，以顯示或隱藏 Internet Explorer 物件的 [網址] 列。  
  
```  
void SetAddressBar(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 非零值以顯示 [網址] 列中。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namesetfullscreena--chtmlviewsetfullscreen"></a><a name="setfullscreen"></a>CHtmlView::SetFullScreen  
 呼叫此成員函式，將 Internet Explorer 設定為 [全螢幕] 或 [標準] 視窗模式。  
  
```  
void SetFullScreen(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 非零代表全螢幕模式。否則為零。  
  
### <a name="remarks"></a>備註  
 在全螢幕模式中，Internet Explorer 的主視窗最大化，並隱藏狀態列、 工具列、 功能表列和標題列。  
  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namesetheighta--chtmlviewsetheight"></a><a name="setheight"></a>CHtmlView::SetHeight  
 呼叫此成員函式，來設定 Internet Explorer 的主視窗的高度。  
  
```  
void SetHeight(long nNewValue);
```  
  
### <a name="parameters"></a>參數  
 `nNewValue`  
 高度，單位為像素的主視窗。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetlefta--chtmlviewsetleft"></a><a name="setleft"></a>CHtmlView::SetLeft  
 設定 Internet Explorer 主視窗的水平位置。  
  
```  
void SetLeft(long nNewValue);
```  
  
### <a name="parameters"></a>參數  
 `nNewValue`  
 在主視窗的左邊緣的螢幕座標。  
  
##  <a name="a-namesetmenubara--chtmlviewsetmenubar"></a><a name="setmenubar"></a>CHtmlView::SetMenuBar  
 呼叫此成員函式，以顯示或隱藏 Internet Explorer 的功能表列。  
  
```  
void SetMenuBar(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 非零值以顯示功能表列。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namesetofflinea--chtmlviewsetoffline"></a><a name="setoffline"></a>CHtmlView::SetOffline  
 呼叫此成員函式設定值，指出是否 WebBrowser 控制項目前是否正在離線模式。  
  
```  
void SetOffline(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 非零值，以讀取本機快取中;否則為零。  
  
### <a name="remarks"></a>備註  
 在離線模式中，瀏覽器可讀取的 HTML 網頁，從本機快取，而不是從來源文件。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetregisterasbrowsera--chtmlviewsetregisterasbrowser"></a><a name="setregisterasbrowser"></a>CHtmlView::SetRegisterAsBrowser  
 呼叫此成員函式設定值，指出是否要將 WebBrowser 控制項註冊為最上層的瀏覽器為目標的名稱解析。  
  
```  
void SetRegisterAsBrowser(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 判斷是否要將 Internet Explorer 登錄做為最上層的瀏覽器。 如果是非零值，網頁瀏覽器會註冊為最上層的瀏覽器。如果為零，它不是最上層的瀏覽器。 預設值是零。  
  
### <a name="remarks"></a>備註  
 最上層的瀏覽器是瀏覽器做為預設瀏覽器的登錄設定。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetregisterasdroptargeta--chtmlviewsetregisterasdroptarget"></a><a name="setregisterasdroptarget"></a>CHtmlView::SetRegisterAsDropTarget  
 呼叫此成員函式設定值，指出是否要將 WebBrowser 控制項註冊為瀏覽的置放目標。  
  
```  
void SetRegisterAsDropTarget(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 判斷是否 WebBrowser 控制項登錄為置放目標的導覽。 非零值，如果物件已登錄為置放目標。如果為零，，則不置放目標。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetsilenta--chtmlviewsetsilent"></a><a name="setsilent"></a>CHtmlView::SetSilent  
 呼叫此成員函式設定值，指出是否可以顯示任何對話方塊。  
  
```  
void SetSilent(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 如果是非零值，將不會顯示對話方塊。如果為零，則會顯示對話方塊。 預設值是零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetstatusbara--chtmlviewsetstatusbar"></a><a name="setstatusbar"></a>CHtmlView::SetStatusBar  
 呼叫此成員函式會顯示狀態列。  
  
```  
void SetStatusBar(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 狀態列會顯示; 如果為非零否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namesettheatermodea--chtmlviewsettheatermode"></a><a name="settheatermode"></a>CHtmlView::SetTheaterMode  
 呼叫此成員函式設定值，指出 WebBrowser 控制項是否處於劇場模式。  
  
```  
void SetTheaterMode(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 非零值將 WebBrowser 控制項設定為劇場模式;否則為零。 預設值是零。  
  
### <a name="remarks"></a>備註  
 劇場模式中的網頁瀏覽器時，瀏覽器的主視窗填滿整個螢幕，具有最基本的巡覽工具的工具列會出現，而狀態列上會出現在螢幕右上角。  
  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesettoolbara--chtmlviewsettoolbar"></a><a name="settoolbar"></a>CHtmlView::SetToolBar  
 呼叫此成員函式，以顯示或隱藏 Internet Explorer 工具列。  
  
```  
void SetToolBar(int nNewValue);
```  
  
### <a name="parameters"></a>參數  
 `nNewValue`  
 指出是否要顯示工具列。 工具列會顯示; 如果為非零否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer。 如果您使用 WebBrowser 控制項使用這個呼叫，它會傳回任何錯誤，但它將會忽略這個呼叫。  
  
##  <a name="a-namesettopa--chtmlviewsettop"></a><a name="settop"></a>CHtmlView::SetTop  
 呼叫此成員函式設定 WebBrowser 控制項內部上的邊緣和其容器頂端之間的距離  
  
```  
void SetTop(long nNewValue);
```  
  
### <a name="parameters"></a>參數  
 `nNewValue`  
 主視窗的頂端的螢幕座標。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetvisiblea--chtmlviewsetvisible"></a><a name="setvisible"></a>CHtmlView::SetVisible  
 呼叫此成員函式設定 WebBrowser 控制項的可見性狀態。  
  
```  
void SetVisible(BOOL bNewValue);
```  
  
### <a name="parameters"></a>參數  
 `bNewValue`  
 非零，如果控制項是可見的。否則為零。  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
##  <a name="a-namesetwidtha--chtmlviewsetwidth"></a><a name="setwidth"></a>CHtmlView::SetWidth  
 設定 Internet Explorer 主視窗的寬度。  
  
```  
void SetWidth(long nNewValue);
```  
  
### <a name="parameters"></a>參數  
 `nNewValue`  
 像素為單位，Internet Explorer 的主視窗的寬度。  
  
##  <a name="a-namestopa--chtmlviewstop"></a><a name="stop"></a>CHtmlView::Stop  
 呼叫此成員函式，若要取消任何暫止的巡覽或下載作業並停止任何動態頁面項目，例如背景聲音和動畫。  
  
```  
void Stop();
```  
  
### <a name="remarks"></a>備註  
 適用於 Internet Explorer 和 WebBrowser。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MFCIE](../../visual-cpp-samples.md)   
 [CFormView 類別](../../mfc/reference/cformview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)


