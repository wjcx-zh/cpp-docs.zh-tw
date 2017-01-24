---
title: "CHtmlView 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHtmlView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "瀏覽器, MFC 支援"
  - "CHtmlView 類別"
  - "WebBrowser 控制項"
  - "WebBrowser 控制項, MFC 支援"
ms.assetid: 904976af-73de-4aba-84ac-cfae8e2be09a
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHtmlView 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 MFC 的文件\/檢視架構內容中提供 WebBrowser 控制項的功能。  
  
## 語法  
  
```  
class CHtmlView : public CFormView  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHtmlView::Create](../Topic/CHtmlView::Create.md)|建立 WebBrowser 控制項。|  
|[CHtmlView::CreateControlSite](../Topic/CHtmlView::CreateControlSite.md)|可覆寫，用來建立主控表單上之控制項的控制項網站執行個體。|  
|[CHtmlView::ExecFormsCommand](../Topic/CHtmlView::ExecFormsCommand.md)|使用 `IOleCommandTarget::Exec` 方法執行指定的命令。|  
|[CHtmlView::ExecWB](../Topic/CHtmlView::ExecWB.md)|執行命令。|  
|[CHtmlView::GetAddressBar](../Topic/CHtmlView::GetAddressBar.md)|決定是否顯示 Internet Explorer 物件的網址列。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::GetApplication](../Topic/CHtmlView::GetApplication.md)|擷取代表應用程式的應用程式物件，此應用程式包含 Internet Explorer 應用程式目前的執行個體。|  
|[CHtmlView::GetBusy](../Topic/CHtmlView::GetBusy.md)|擷取指出下載或其他活動是否仍在進行中的值。|  
|[CHtmlView::GetContainer](../Topic/CHtmlView::GetContainer.md)|擷取 WebBrowser 控制項的容器。|  
|[CHtmlView::GetFullName](../Topic/CHtmlView::GetFullName.md)|擷取顯示在網頁瀏覽器中的資源完整名稱，包括路徑。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::GetFullScreen](../Topic/CHtmlView::GetFullScreen.md)|指出 WebBrowser 控制項是在全螢幕模式或標準視窗模式中操作。|  
|[CHtmlView::GetHeight](../Topic/CHtmlView::GetHeight.md)|擷取 Internet Explorer 主視窗的高度。|  
|[CHtmlView::GetHtmlDocument](../Topic/CHtmlView::GetHtmlDocument.md)|擷取使用中的 HTML 文件。|  
|[CHtmlView::GetLeft](../Topic/CHtmlView::GetLeft.md)|擷取 Internet Explorer 主視窗左邊緣的螢幕座標。|  
|[CHtmlView::GetLocationName](../Topic/CHtmlView::GetLocationName.md)|擷取 WebBrowser 目前顯示的資源名稱。|  
|[CHtmlView::GetLocationURL](../Topic/CHtmlView::GetLocationURL.md)|擷取 WebBrowser 目前顯示的資源 URL。|  
|[CHtmlView::GetMenuBar](../Topic/CHtmlView::GetMenuBar.md)|擷取決定是否顯示功能表列的值。|  
|[CHtmlView::GetOffline](../Topic/CHtmlView::GetOffline.md)|擷取決定控制項是否離線的值。|  
|[CHtmlView::GetParentBrowser](../Topic/CHtmlView::GetParentBrowser.md)|擷取 `IDispatch` 介面的指標。 如需詳細資訊，請參閱[Implementing the IDispatch Interface](http://msdn.microsoft.com/zh-tw/0e171f7f-0022-4e9b-ac8e-98192828e945)。|  
|[CHtmlView::GetProperty](../Topic/CHtmlView::GetProperty.md)|擷取與指定物件相關聯屬性目前的值。|  
|[CHtmlView::GetReadyState](../Topic/CHtmlView::GetReadyState.md)|擷取網頁瀏覽器物件的就緒狀態。|  
|[CHtmlView::GetRegisterAsBrowser](../Topic/CHtmlView::GetRegisterAsBrowser.md)|指出 WebBrowser 控制項是否註冊為目標名稱解析的最上層瀏覽器進行。|  
|[CHtmlView::GetRegisterAsDropTarget](../Topic/CHtmlView::GetRegisterAsDropTarget.md)|指出 WebBrowser 控制項是否註冊為巡覽的置放目標。|  
|[CHtmlView::GetSilent](../Topic/CHtmlView::GetSilent.md)|指出是否可顯示所有對話方塊。|  
|[CHtmlView::GetSource](../Topic/CHtmlView::GetSource.md)|網頁的 HTML 原始程式碼。|  
|[CHtmlView::GetStatusBar](../Topic/CHtmlView::GetStatusBar.md)|指出是否顯示 Internet Explorer 狀態列。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::GetTheaterMode](../Topic/CHtmlView::GetTheaterMode.md)|指出 WebBrowser 控制項是否為劇場模式。|  
|[CHtmlView::GetToolBar](../Topic/CHtmlView::GetToolBar.md)|擷取決定是否顯示工具列的值。|  
|[CHtmlView::GetTop](../Topic/CHtmlView::GetTop.md)|擷取 Internet Explorer 主視窗上邊緣的螢幕座標。|  
|[CHtmlView::GetTopLevelContainer](../Topic/CHtmlView::GetTopLevelContainer.md)|擷取值，指出目前的物件是否為 WebBrowser 控制項的最上層容器。|  
|[CHtmlView::GetType](../Topic/CHtmlView::GetType.md)|擷取文件物件的類型名稱。|  
|[CHtmlView::GetVisible](../Topic/CHtmlView::GetVisible.md)|擷取指出物件為顯示或隱藏的值。|  
|[CHtmlView::GetWidth](../Topic/CHtmlView::GetWidth.md)|擷取 Internet Explorer 主視窗的寬度。|  
|[CHtmlView::GoBack](../Topic/CHtmlView::GoBack.md)|在歷程清單中巡覽至上一個項目。|  
|[CHtmlView::GoForward](../Topic/CHtmlView::GoForward.md)|在歷程清單中巡覽至下一個項目。|  
|[CHtmlView::GoHome](../Topic/CHtmlView::GoHome.md)|巡覽至目前的首頁或起始頁面。|  
|[CHtmlView::GoSearch](../Topic/CHtmlView::GoSearch.md)|巡覽至目前的搜尋頁面。|  
|[CHtmlView::LoadFromResource](../Topic/CHtmlView::LoadFromResource.md)|載入 WebBrowser 控制項的資源。|  
|[CHtmlView::Navigate](../Topic/CHtmlView::Navigate.md)|巡覽至依 URL 找到的資源。|  
|[CHtmlView::Navigate2](../Topic/CHtmlView::Navigate2.md)|巡覽至依 URL 找到的資源或依完整路徑找到的檔案。|  
|[CHtmlView::OnBeforeNavigate2](../Topic/CHtmlView::OnBeforeNavigate2.md)|在給定的 WebBrowser 中發生巡覽前呼叫 \(無論是在視窗或框架項目上\)。|  
|[CHtmlView::OnCommandStateChange](../Topic/CHtmlView::OnCommandStateChange.md)|呼叫以通知應用程式， 網頁瀏覽器命令啟用的狀態已經變更。|  
|[CHtmlView::OnDocumentComplete](../Topic/CHtmlView::OnDocumentComplete.md)|呼叫以通知應用程式，文件已達到 `READYSTATE_COMPLETE` 狀態。|  
|[CHtmlView::OnDocWindowActivate](../Topic/CHtmlView::OnDocWindowActivate.md)|從 Internet Explorer 或 MSHTML 實作的 [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) 呼叫，這會在容器文件視窗啟用或停用時，通知使用中的就地物件。|  
|[CHtmlView::OnDownloadBegin](../Topic/CHtmlView::OnDownloadBegin.md)|呼叫以通知應用程式，巡覽作業已經啟動。|  
|[CHtmlView::OnDownloadComplete](../Topic/CHtmlView::OnDownloadComplete.md)|當巡覽作業結束、暫止或失敗時呼叫。|  
|[CHtmlView::OnEnableModeless](../Topic/CHtmlView::OnEnableModeless.md)|當容器建立或終結強制回應對話方塊時，呼叫以啟用或停用非強制回應對話方塊。|  
|[CHtmlView::OnFilterDataObject](../Topic/CHtmlView::OnFilterDataObject.md)|Internet Explorer 或 MSHTML 在主機上呼叫，允許主機替換 Internet Explorer 或 MSHTML 的資料物件。|  
|[CHtmlView::OnFrameWindowActivate](../Topic/CHtmlView::OnFrameWindowActivate.md)|從 [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) 呼叫，在容器的最上層框架視窗啟用或停用時通知物件。|  
|[CHtmlView::OnFullScreen](../Topic/CHtmlView::OnFullScreen.md)|當 FullScreen 屬性變更時呼叫。|  
|[CHtmlView::OnGetDropTarget](../Topic/CHtmlView::OnGetDropTarget.md)|當它用做為置放目標，讓主機提供另一個 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) 時，由 Internet Explorer 或 MSHTML 呼叫。|  
|[CHtmlView::OnGetExternal](../Topic/CHtmlView::OnGetExternal.md)|由 Internet Explorer 或 MSHTML 呼叫，以取得主機的 `IDispatch` 介面。|  
|[CHtmlView::OnGetHostInfo](../Topic/CHtmlView::OnGetHostInfo.md)|擷取 Internet Explorer 或 MSHTML 主機的 UI 功能。|  
|[CHtmlView::OnGetOptionKeyPath](../Topic/CHtmlView::OnGetOptionKeyPath.md)|傳回 Internet Explorer 或 MSHTML 儲存使用者喜好設定的登錄機碼。|  
|[CHtmlView::OnHideUI](../Topic/CHtmlView::OnHideUI.md)|當 Internet Explorer 或 MSHTML 移除其功能表與工具列時呼叫。|  
|[CHtmlView::OnMenuBar](../Topic/CHtmlView::OnMenuBar.md)|當 MenuBar 屬性變更時呼叫。|  
|[CHtmlView::OnNavigateComplete2](../Topic/CHtmlView::OnNavigateComplete2.md)|超連結的巡覽完畢後呼叫 \(無論是在視窗或框架項目上\)。|  
|[CHtmlView::OnNavigateError](../Topic/CHtmlView::OnNavigateError.md)|巡覽至超連結失敗時，由架構呼叫。|  
|[CHtmlView::OnNewWindow2](../Topic/CHtmlView::OnNewWindow2.md)|當為顯示資源而建立新視窗時呼叫。|  
|[CHtmlView::OnProgressChange](../Topic/CHtmlView::OnProgressChange.md)|呼叫以通知應用程式，下載作業的進度已經更新。|  
|[CHtmlView::OnPropertyChange](../Topic/CHtmlView::OnPropertyChange.md)|呼叫以通知應用程式，[PutProperty](../Topic/CHtmlView::PutProperty.md) 方法已經變更屬性的值。|  
|[CHtmlView::OnQuit](../Topic/CHtmlView::OnQuit.md)|呼叫以通知應用程式，Internet Explorer 應用程式已經可以結束。 \(僅限 Internet Explorer\)|  
|[CHtmlView::OnResizeBorder](../Topic/CHtmlView::OnResizeBorder.md)|從 Internet Explorer 或 MSHTML 實作的 [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) 呼叫，警示物件它需要調整框線空間的大小。|  
|[CHtmlView::OnShowContextMenu](../Topic/CHtmlView::OnShowContextMenu.md)|當它正要顯示內容功能表時，從 Internet Explorer 或 MSHTML 呼叫。|  
|[CHtmlView::OnShowUI](../Topic/CHtmlView::OnShowUI.md)|在 Internet Explorer 或 MSHTML 顯示其功能表與工具列之前呼叫。|  
|[CHtmlView::OnStatusBar](../Topic/CHtmlView::OnStatusBar.md)|當 StatusBar 屬性變更時呼叫。|  
|[CHtmlView::OnStatusTextChange](../Topic/CHtmlView::OnStatusTextChange.md)|呼叫以通知應用程式，和 WebBrowser 控制項相關的狀態列文字已經變更。|  
|[CHtmlView::OnTheaterMode](../Topic/CHtmlView::OnTheaterMode.md)|當 TheaterMode 屬性變更時呼叫。|  
|[CHtmlView::OnTitleChange](../Topic/CHtmlView::OnTitleChange.md)|呼叫以通知應用程式，WebBrowser 控制項中文件的標題是否變成可用或變更。|  
|[CHtmlView::OnToolBar](../Topic/CHtmlView::OnToolBar.md)|當 ToolBar 屬性變更時呼叫。|  
|[CHtmlView::OnTranslateAccelerator](../Topic/CHtmlView::OnTranslateAccelerator.md)|當呼叫 [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) 或 [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) 處理來自容器訊息佇列的功能表快速鍵訊息時，由 Internet Explorer 或 MSHTML 呼叫。|  
|[CHtmlView::OnTranslateUrl](../Topic/CHtmlView::OnTranslateUrl.md)|由 Internet Explorer 或 MSHTML 呼叫，讓主機有機會修改要載入的 URL。|  
|[CHtmlView::OnUpdateUI](../Topic/CHtmlView::OnUpdateUI.md)|通知主機命令狀態已變更。|  
|[CHtmlView::OnVisible](../Topic/CHtmlView::OnVisible.md)|當 WebBrowser 控制項的視窗必須顯示\/隱藏時呼叫。|  
|[CHtmlView::PutProperty](../Topic/CHtmlView::PutProperty.md)|設定與指定物件相關聯屬性的值。|  
|[CHtmlView::QueryFormsCommand](../Topic/CHtmlView::QueryFormsCommand.md)|查詢使用者介面事件所產生之一或多個命令的狀態。|  
|[CHtmlView::QueryStatusWB](../Topic/CHtmlView::QueryStatusWB.md)|查詢 WebBrowser 控制項處理中的命令狀態。|  
|[CHtmlView::Refresh](../Topic/CHtmlView::Refresh.md)|重新載入目前的檔案。|  
|[CHtmlView::Refresh2](../Topic/CHtmlView::Refresh2.md)|重新載入目前的檔案，並選擇性地防止傳送 `pragma:nocache` 標頭。|  
|[CHtmlView::SetAddressBar](../Topic/CHtmlView::SetAddressBar.md)|顯示或隱藏 Internet Explorer 物件的網址列。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::SetFullScreen](../Topic/CHtmlView::SetFullScreen.md)|設定值以決定控制項在全螢幕模式或標準視窗模式中操作。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::SetHeight](../Topic/CHtmlView::SetHeight.md)|設定 Internet Explorer 主視窗的高度。|  
|[CHtmlView::SetLeft](../Topic/CHtmlView::SetLeft.md)|設定 Internet Explorer 主視窗的水平位置。|  
|[CHtmlView::SetMenuBar](../Topic/CHtmlView::SetMenuBar.md)|設定決定是否顯示控制項功能表列的值。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::SetOffline](../Topic/CHtmlView::SetOffline.md)|設定決定控制項是否離線的值。|  
|[CHtmlView::SetRegisterAsBrowser](../Topic/CHtmlView::SetRegisterAsBrowser.md)|設定值，指出 WebBrowser 控制項是否註冊為目標名稱解析的最上層瀏覽器。|  
|[CHtmlView::SetRegisterAsDropTarget](../Topic/CHtmlView::SetRegisterAsDropTarget.md)|設定值，指出 WebBrowser 控制項是否註冊為巡覽的置放目標。|  
|[CHtmlView::SetSilent](../Topic/CHtmlView::SetSilent.md)|設定決定控制項是否顯示對話方塊的值。|  
|[CHtmlView::SetStatusBar](../Topic/CHtmlView::SetStatusBar.md)|設定值，決定是否顯示 Internet Explorer 狀態列。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::SetTheaterMode](../Topic/CHtmlView::SetTheaterMode.md)|設定指出 WebBrowser 控制項是否為劇場模式的值。|  
|[CHtmlView::SetToolBar](../Topic/CHtmlView::SetToolBar.md)|設定決定是否顯示控制項工具列的值。 \(忽略　WebBrowser 控制項，僅限 Internet Explorer。\)|  
|[CHtmlView::SetTop](../Topic/CHtmlView::SetTop.md)|設定 Internet Explorer 主視窗的垂直位置。|  
|[CHtmlView::SetVisible](../Topic/CHtmlView::SetVisible.md)|設定指出物件為顯示或隱藏的值。|  
|[CHtmlView::SetWidth](../Topic/CHtmlView::SetWidth.md)|設定 Internet Explorer 主視窗的寬度。|  
|[CHtmlView::Stop](../Topic/CHtmlView::Stop.md)|停止開啟檔案。|  
  
## 備註  
 WebBrowser 控制項是一個視窗，使用者在這裡可以瀏覽全球資訊網的網站，以及本機檔案系統和網路上的資料夾。 WebBrowser 控制項支援超連結和統一資源定位器 \(URL\) 巡覽，以及維護歷程記錄清單。  
  
## 使用 MFC 應用程式的 CHtmlView 類別  
 在標準的 MFC 架構應用程式中 \(SDI 或 MDI 型\)，檢視物件通常衍生自一組特製的類別。 這些類別全都衍生自 `CView`，除 `CView` 提供的功能之外，還提供特製的功能。  
  
 以 `CHtmlView` 當做應用程式檢視類別的基礎，可以提供附有 WebBrowser 控制項的檢視。 這能讓應用程式變成網頁瀏覽器。 建立網頁瀏覽器型應用程式的慣用方法，是使用 \[MFC 應用程式精靈\]，指定 `CHtmlView` 為檢視類別。 如需在 MFC 應用程式中實作及使用 WebBrowser 控制項的詳細資訊，請參閱[建立網頁瀏覽器型的應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)。  
  
> [!NOTE]
>  WebBrowser ActiveX 控制項 \(亦即 `CHtmlView`\) 僅適用於已安裝 Internet Explorer 4.0 或更新版本的 Windows NT 4.0 或更新版本中所執行的程式。  
  
 `CHtmlView` 是為存取 Web \(和\/或 HTML 文件\) 的應用程式所設計。 下列 `CHtmlView` 成員函式僅適用於 Internet Explorer 應用程式。 WebBrowser 控制項沿用這些函式，但作用不明顯。  
  
-   [GetAddressBar](../Topic/CHtmlView::GetAddressBar.md)  
  
-   [GetFullName](../Topic/CHtmlView::GetFullName.md)  
  
-   [GetStatusBar](../Topic/CHtmlView::GetStatusBar.md)  
  
-   [SetAddressBar](../Topic/CHtmlView::SetAddressBar.md)  
  
-   [SetFullScreen](../Topic/CHtmlView::SetFullScreen.md)  
  
-   [SetMenuBar](../Topic/CHtmlView::SetMenuBar.md)  
  
-   [SetStatusBar](../Topic/CHtmlView::SetStatusBar.md)  
  
-   [SetToolBar](../Topic/CHtmlView::SetToolBar.md)  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CHtmlView`  
  
## 需求  
 **Header:** afxhtml.h  
  
## 請參閱  
 [MFC 範例 MFCIE](../../top/visual-cpp-samples.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx)