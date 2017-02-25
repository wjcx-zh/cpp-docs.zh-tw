---
title: "CDHtmlDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDHtmlDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDHtmlDialog class"
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDHtmlDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用建立使用 HTML 取代對話方塊資源實作其使用者介面的對話方塊。  
  
## 語法  
  
```  
class CDHtmlDialog : public CDialog, public CDHtmlEventSink  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDHtmlDialog::CDHtmlDialog](../Topic/CDHtmlDialog::CDHtmlDialog.md)|CDHtmlDialog 建構物件。|  
|[CDHtmlDialog::~CDHtmlDialog](../Topic/CDHtmlDialog::~CDHtmlDialog.md)|CDHtmlDialog 會終結物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDHtmlDialog::CanAccessExternal](../Topic/CDHtmlDialog::CanAccessExternal.md)|可覆寫的，當存取檢查指令碼是否在呼叫中的載入頁面物件可以存取控制項站台的外部分派。  判斷分派檢查為或指令碼的安全或目前區域允許做為指令碼物件不是安全的。|  
|[CDHtmlDialog::CreateControlSite](../Topic/CDHtmlDialog::CreateControlSite.md)|用來建立可覆寫控制網站執行個體來裝載在對話方塊的瀏覽器控制項。|  
|[CDHtmlDialog::DDX\_DHtml\_AxControl](../Topic/CDHtmlDialog::DDX_DHtml_AxControl.md)|在成員變數和 ActiveX 控制項的屬性值之間交換資料在 HTML 網頁的。|  
|[CDHtmlDialog::DDX\_DHtml\_CheckBox](../Topic/CDHtmlDialog::DDX_DHtml_CheckBox.md)|在 10% 成員變數和核取方塊之間交換資料在 HTML 網頁。|  
|[CDHtmlDialog::DDX\_DHtml\_ElementText](../Topic/CDHtmlDialog::DDX_DHtml_ElementText.md)|在 10% 成員變數和任何 HTML 項目的屬性之間交換資料在 HTML 網頁。|  
|[CDHtmlDialog::DDX\_DHtml\_Radio](../Topic/CDHtmlDialog::DDX_DHtml_Radio.md)|在 10% 成員變數和一個選項按鈕間交換資料在 HTML 網頁。|  
|[CDHtmlDialog::DDX\_DHtml\_SelectIndex](../Topic/CDHtmlDialog::DDX_DHtml_SelectIndex.md)|取得或設定一個清單方塊中的索引 \(HTML 網頁的。|  
|[CDHtmlDialog::DDX\_DHtml\_SelectString](../Topic/CDHtmlDialog::DDX_DHtml_SelectString.md)|取得或設定一個清單方塊項目的顯示文字 \(根據目前索引\) 在 HTML 網頁。|  
|[CDHtmlDialog::DDX\_DHtml\_SelectValue](../Topic/CDHtmlDialog::DDX_DHtml_SelectValue.md)|取得或設定一個清單方塊中輸入的值 \(根據目前索引\) 在 HTML 網頁。|  
|[CDHtmlDialog::DestroyModeless](../Topic/CDHtmlDialog::DestroyModeless.md)|終結非強制回應對話方塊。|  
|[CDHtmlDialog::EnableModeless](../Topic/CDHtmlDialog::EnableModeless.md)|可為非強制回應對話方塊。|  
|[CDHtmlDialog::FilterDataObject](../Topic/CDHtmlDialog::FilterDataObject.md)|允許對話篩選剪貼簿由瀏覽器裝載建立資料物件。|  
|[CDHtmlDialog::GetControlDispatch](../Topic/CDHtmlDialog::GetControlDispatch.md)|擷取在 HTML 文件中內嵌的 ActiveX 控制項的 `IDispatch` 介面。|  
|[CDHtmlDialog::GetControlProperty](../Topic/CDHtmlDialog::GetControlProperty.md)|擷取指定的 ActiveX 控制項要求的屬性。|  
|[CDHtmlDialog::GetCurrentUrl](../Topic/CDHtmlDialog::GetCurrentUrl.md)|擷取統一資源定位器 \(URL\) \(URL\) 與目前文件。|  
|[CDHtmlDialog::GetDHtmlDocument](../Topic/CDHtmlDialog::GetDHtmlDocument.md)|擷取目前載入的 HTML 文件的 IHTMLDocument2 介面。|  
|[CDHtmlDialog::GetDropTarget](../Topic/CDHtmlDialog::GetDropTarget.md)|呼叫由包含的瀏覽器控制項，以在用於，置放目標可讓對話方塊提供替代的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)。|  
|[CDHtmlDialog::GetElement](../Topic/CDHtmlDialog::GetElement.md)|取得 HTML 項目的介面。|  
|[CDHtmlDialog::GetElementHtml](../Topic/CDHtmlDialog::GetElementHtml.md)|擷取 HTML 項目的 **innerHTML** 屬性。|  
|[CDHtmlDialog::GetElementInterface](../Topic/CDHtmlDialog::GetElementInterface.md)|從 HTML 項目擷取要求的介面指標。|  
|[CDHtmlDialog::GetElementProperty](../Topic/CDHtmlDialog::GetElementProperty.md)|擷取 HTML 項目的屬性值。|  
|[CDHtmlDialog::GetElementText](../Topic/CDHtmlDialog::GetElementText.md)|擷取 HTML 項目的 **innerText** 屬性。|  
|[CDHtmlDialog::GetEvent](../Topic/CDHtmlDialog::GetEvent.md)|具有 **IHTMLEventObj** 指標目前事件的物件。|  
|[CDHtmlDialog::GetExternal](../Topic/CDHtmlDialog::GetExternal.md)|取得主機的 `IDispatch` 介面。|  
|[CDHtmlDialog::GetHostInfo](../Topic/CDHtmlDialog::GetHostInfo.md)|擷取主應用程式的 UI 功能。|  
|[CDHtmlDialog::GetOptionKeyPath](../Topic/CDHtmlDialog::GetOptionKeyPath.md)|擷取下一個使用者喜好設定儲存的登錄機碼。|  
|[CDHtmlDialog::HideUI](../Topic/CDHtmlDialog::HideUI.md)|隱藏主應用程式的 UI。|  
|[CDHtmlDialog::IsExternalDispatchSafe](../Topic/CDHtmlDialog::IsExternalDispatchSafe.md)|表示主應用程式的 `IDispatch` 介面是否為指令碼是安全的。|  
|[CDHtmlDialog::LoadFromResource](../Topic/CDHtmlDialog::LoadFromResource.md)|載入指定的資源到瀏覽器控制項。|  
|[CDHtmlDialog::Navigate](../Topic/CDHtmlDialog::Navigate.md)|巡覽至指定的 URL。|  
|[CDHtmlDialog::OnBeforeNavigate](../Topic/CDHtmlDialog::OnBeforeNavigate.md)|呼叫由架構在巡覽事件之前引發。|  
|[CDHtmlDialog::OnDocumentComplete](../Topic/CDHtmlDialog::OnDocumentComplete.md)|呼叫以告知架構應用程式，當文件到達 `READYSTATE_COMPLETE` 狀態。|  
|[CDHtmlDialog::OnDocWindowActivate](../Topic/CDHtmlDialog::OnDocWindowActivate.md)|呼叫框架，其在文件視窗中啟用或停用。|  
|[CDHtmlDialog::OnFrameWindowActivate](../Topic/CDHtmlDialog::OnFrameWindowActivate.md)|呼叫框架，其在框架視窗中啟用或停用。|  
|[CDHtmlDialog::OnInitDialog](../Topic/CDHtmlDialog::OnInitDialog.md)|呼叫以回應 **WM\_INITDIALOG** 訊息。|  
|[CDHtmlDialog::OnNavigateComplete](../Topic/CDHtmlDialog::OnNavigateComplete.md)|呼叫由架構在巡覽事件之後。|  
|[CDHtmlDialog::ResizeBorder](../Topic/CDHtmlDialog::ResizeBorder.md)|警告物件需要調整其框線空間。|  
|[CDHtmlDialog::SetControlProperty](../Topic/CDHtmlDialog::SetControlProperty.md)|將 ActiveX 控制項的屬性設定為新值。|  
|[CDHtmlDialog::SetElementHtml](../Topic/CDHtmlDialog::SetElementHtml.md)|設定 HTML 項目的 **innerHTML** 屬性。|  
|[CDHtmlDialog::SetElementProperty](../Topic/CDHtmlDialog::SetElementProperty.md)|設定 HTML 項目的屬性。|  
|[CDHtmlDialog::SetElementText](../Topic/CDHtmlDialog::SetElementText.md)|設定 HTML 項目的 **innerText** 屬性。|  
|[CDHtmlDialog::SetExternalDispatch](../Topic/CDHtmlDialog::SetExternalDispatch.md)|設定主應用程式的 `IDispatch` 介面。|  
|[CDHtmlDialog::SetHostFlags](../Topic/CDHtmlDialog::SetHostFlags.md)|設定主應用程式的 UI 旗標。|  
|[CDHtmlDialog::ShowContextMenu](../Topic/CDHtmlDialog::ShowContextMenu.md)|呼叫時，內容功能表隨即顯示。|  
|[CDHtmlDialog::ShowUI](../Topic/CDHtmlDialog::ShowUI.md)|顯示主應用程式的 UI。|  
|[CDHtmlDialog::TranslateAccelerator](../Topic/CDHtmlDialog::TranslateAccelerator.md)|呼叫處理功能表快速鍵按鍵訊息。|  
|[CDHtmlDialog::TranslateUrl](../Topic/CDHtmlDialog::TranslateUrl.md)|呼叫修改要載入的 URL。|  
|[CDHtmlDialog::UpdateUI](../Topic/CDHtmlDialog::UpdateUI.md)|呼叫以告知主應用程式命令狀態已變更。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDHtmlDialog::m\_bUseHtmlTitle](../Topic/CDHtmlDialog::m_bUseHtmlTitle.md)|指出是否要使用 HTML 文件的標題做為對話方塊的標題。|  
|[CDHtmlDialog::m\_nHtmlResID](../Topic/CDHtmlDialog::m_nHtmlResID.md)|HTML 資源 ID 要顯示的。|  
|[CDHtmlDialog::m\_pBrowserApp](../Topic/CDHtmlDialog::m_pBrowserApp.md)|對 Web 瀏覽器應用程式的指標。|  
|[CDHtmlDialog::m\_spHtmlDoc](../Topic/CDHtmlDialog::m_spHtmlDoc.md)|為 HTML 文件的指標。|  
|[CDHtmlDialog::m\_strCurrentUrl](../Topic/CDHtmlDialog::m_strCurrentUrl.md)|目前的 URL。|  
|[CDHtmlDialog::m\_szHtmlResID](../Topic/CDHtmlDialog::m_szHtmlResID.md)|HTML 資源 ID. 的字串版本。|  
  
## 備註  
 **CDHtmlDialog** 也可以載入從 HTML 資源或 URL 中所顯示的 HTML。  
  
 `CDHtmlDialog` 也可以進行資料交換和 HTML 控制項和處理來自 HTML 控制項的事件，例如按一下按鈕。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CDHtmlDialog`  
  
## 需求  
 **Header:** afxdhtml.h  
  
## 請參閱  
 [MFC DHtmlExplore 範例](../../top/visual-cpp-samples.md)   
 [DDX\_DHtml Helper Macros](../../mfc/reference/ddx-dhtml-helper-macros.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)