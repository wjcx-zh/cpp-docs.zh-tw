---
title: "CFrameWnd Class | Microsoft Docs"
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
  - "CFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWnd class"
  - "frame window classes, 基底類別"
  - "frame windows, 建立"
  - "單一文件介面 (SDI), frame windows"
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理 Windows 提供單一文件介面 \(SDI\) 視窗與成員一起重疊或快顯框架視窗， \(SDI\) 的功能。  
  
## 語法  
  
```  
class CFrameWnd : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFrameWnd::CFrameWnd](../Topic/CFrameWnd::CFrameWnd.md)|建構 `CFrameWnd` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFrameWnd::ActivateFrame](../Topic/CFrameWnd::ActivateFrame.md)|將框架可見和使用者。|  
|[CFrameWnd::BeginModalState](../Topic/CFrameWnd::BeginModalState.md)|將框架視窗為強制回應。|  
|[CFrameWnd::Create](../Topic/CFrameWnd::Create.md)|呼叫以建立和初始化框架視窗與 `CFrameWnd` 物件。|  
|[CFrameWnd::CreateView](../Topic/CFrameWnd::CreateView.md)|會在從 `CView`並非衍生的框架中的檢視。|  
|[CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md)|內建的控制列。|  
|[CFrameWnd::EnableDocking](../Topic/CFrameWnd::EnableDocking.md)|允許將控制列停駐。|  
|[CFrameWnd::EndModalState](../Topic/CFrameWnd::EndModalState.md)|關閉框架視窗的強制回應狀態中。  啟用 `BeginModalState`停用的所有視窗。|  
|[CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md)|浮動的控制列。|  
|[CFrameWnd::GetActiveDocument](../Topic/CFrameWnd::GetActiveDocument.md)|傳回現用 **CDocument** 物件。|  
|[CFrameWnd::GetActiveFrame](../Topic/CFrameWnd::GetActiveFrame.md)|傳回現用 `CFrameWnd` 物件。|  
|[CFrameWnd::GetActiveView](../Topic/CFrameWnd::GetActiveView.md)|傳回現用 `CView` 物件。|  
|[CFrameWnd::GetControlBar](../Topic/CFrameWnd::GetControlBar.md)|擷取控制項的資料行。|  
|[CFrameWnd::GetDockState](../Topic/CFrameWnd::GetDockState.md)|擷取框架視窗的內建狀態。|  
|[CFrameWnd::GetMenuBarState](../Topic/CFrameWnd::GetMenuBarState.md)|擷取功能表的顯示狀態在目前 MFC 應用程式中。|  
|[CFrameWnd::GetMenuBarVisibility](../Topic/CFrameWnd::GetMenuBarVisibility.md)|表示  功能表上的預設行為是在目前 MFC 應用程式中是否隱藏或可見。|  
|[CFrameWnd::GetMessageBar](../Topic/CFrameWnd::GetMessageBar.md)|傳回指向屬於框架視窗的狀態列。|  
|[CFrameWnd::GetMessageString](../Topic/CFrameWnd::GetMessageString.md)|擷取訊息與命令 ID. 對應|  
|[CFrameWnd::GetTitle](../Topic/CFrameWnd::GetTitle.md)|擷取相關控制項的標題列。|  
|[CFrameWnd::InitialUpdateFrame](../Topic/CFrameWnd::InitialUpdateFrame.md)|在要呼叫的框架視窗中產生屬於所有檢視的 `OnInitialUpdate` 成員函式。|  
|[CFrameWnd::InModalState](../Topic/CFrameWnd::InModalState.md)|傳回表示框架視窗是否在強制回應狀態。|  
|[CFrameWnd::IsTracking](../Topic/CFrameWnd::IsTracking.md)|判斷分隔列目前是否已移動。|  
|[CFrameWnd::LoadAccelTable](../Topic/CFrameWnd::LoadAccelTable.md)|呼叫載入快速鍵對應表。|  
|[CFrameWnd::LoadBarState](../Topic/CFrameWnd::LoadBarState.md)|還原控制列設定呼叫。|  
|[CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md)|動態建立從資源資訊的框架視窗上呼叫。|  
|[CFrameWnd::NegotiateBorderSpace](../Topic/CFrameWnd::NegotiateBorderSpace.md)|交涉在框架視窗的框線空間。|  
|[CFrameWnd::OnBarCheck](../Topic/CFrameWnd::OnBarCheck.md)|呼叫時，都會作用於指定的控制項執行。|  
|[CFrameWnd::OnContextHelp](../Topic/CFrameWnd::OnContextHelp.md)|就地項目的控制代碼 SHIFT\+F1 說明。|  
|[CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)|設定應用程式的主框架視窗至預覽列印模式。|  
|[CFrameWnd::OnUpdateControlBarMenu](../Topic/CFrameWnd::OnUpdateControlBarMenu.md)|呼叫由架構，在相關的功能表更新。|  
|[CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)|變更物件的位置 `CFrameWnd` 控制列。|  
|[CFrameWnd::SaveBarState](../Topic/CFrameWnd::SaveBarState.md)|儲存控制項的資料行設定呼叫。|  
|[CFrameWnd::SetActivePreviewView](../Topic/CFrameWnd::SetActivePreviewView.md)|將指定的檢視是豐富預覽的現用檢視表。|  
|[CFrameWnd::SetActiveView](../Topic/CFrameWnd::SetActiveView.md)|若要設定現用 `CView` 物件。|  
|[CFrameWnd::SetDockState](../Topic/CFrameWnd::SetDockState.md)|停駐在主視窗的框架視窗上呼叫。|  
|[CFrameWnd::SetMenuBarState](../Topic/CFrameWnd::SetMenuBarState.md)|將功能表的顯示狀態中顯示目前的 MFC 應用程式中的隱藏或。|  
|[CFrameWnd::SetMenuBarVisibility](../Topic/CFrameWnd::SetMenuBarVisibility.md)|將功能表的預設行為是在目前 MFC 應用程式中是隱藏或可見。|  
|[CFrameWnd::SetMessageText](../Topic/CFrameWnd::SetMessageText.md)|將其中一個標準狀態列的文字。|  
|[CFrameWnd::SetProgressBarPosition](../Topic/CFrameWnd::SetProgressBarPosition.md)|設定顯示的 Windows 7 進度列目前位置在工作列中。|  
|[CFrameWnd::SetProgressBarRange](../Topic/CFrameWnd::SetProgressBarRange.md)|設定在工作列上顯示的 Windows 7 進度列的範圍。|  
|[CFrameWnd::SetProgressBarState](../Topic/CFrameWnd::SetProgressBarState.md)|設定在工作列按鈕所顯示的進度指示器的類型和狀態。|  
|[CFrameWnd::SetTaskbarOverlayIcon](../Topic/CFrameWnd::SetTaskbarOverlayIcon.md)|多載。  適用於覆疊工作列按鈕表示應用程式狀態或通知給使用者。|  
|[CFrameWnd::SetTitle](../Topic/CFrameWnd::SetTitle.md)|將相關控制項的標題列。|  
|[CFrameWnd::ShowControlBar](../Topic/CFrameWnd::ShowControlBar.md)|顯示控制項上呼叫。|  
|[CFrameWnd::ShowOwnedWindows](../Topic/CFrameWnd::ShowOwnedWindows.md)|顯示為 `CFrameWnd` 物件的子系的所有視窗。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md)|建立框架的用戶端視窗。|  
|[CFrameWnd::OnHideMenuBar](../Topic/CFrameWnd::OnHideMenuBar.md)|會在目前的 MFC 應用程式的功能表之前隱藏。|  
|[CFrameWnd::OnShowMenuBar](../Topic/CFrameWnd::OnShowMenuBar.md)|會在目前的 MFC 應用程式的  功能表上顯示。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFrameWnd::m\_bAutoMenuEnable](../Topic/CFrameWnd::m_bAutoMenuEnable.md)|自動的控制項啟用和停用功能表項目的功能。|  
|[CFrameWnd::rectDefault](../Topic/CFrameWnd::rectDefault.md)|表示建立 `CFrameWnd` 物件允許視窗選取視窗的初始大小和位置時，請將這個靜態 `CRect` 做為參數。|  
  
## 備註  
 若要建置應用程式的有用框架視窗，請從 `CFrameWnd`衍生一個類別。  將成員變數加入衍生類別加入儲存資料的特定應用程式。  實作的訊息處理常式 \(成員函式和訊息對應在衍生類別中指定的情形，當訊息導向至視窗。  
  
 有三種方式建構框架視窗:  
  
-   使用 [建立](../Topic/CFrameWnd::Create.md)，請直接建構它。  
  
-   使用 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md)，請直接建構它。  
  
-   使用資料範本，請間接建構它。  
  
 在呼叫或之前， **建立**`LoadFrame`使用 C\+\+ **new** 運算子，必須建構堆積中的框架視窗物件。  在呼叫 **建立**之前，您也可以註冊視窗類別的 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 全域函式將框架的圖示和類別樣式。  
  
 使用 **建立** 成員函式是透過架構的建立參數做為直接引數。  
  
 `LoadFrame` 比 **建立**需要較少引數和從資源擷取其大部分預設值，包括框架的標題、圖示、快速鍵對應表和功能表。  若要存取由 `LoadFrame`，這些資源必須具有相同的資源 ID \(例如， **IDR\_MAINFRAME**\)。  
  
 當 `CFrameWnd` 物件包含檢視和文件時，便會由架構間接建立而不是直接由程式設計人員。  `CDocTemplate` 物件組織架構的建立，包含之檢視的建立和檢視的連結至適當的資料。  `CDocTemplate` 建構函式的參數指定涉及三個類別的 `CRuntimeClass` \(文件、架構和檢視\)。  這個架構可用來 `CRuntimeClass` 物件動態建立新的框架 \(Frame\)，指定由使用者 \(例如，藉由使用檔案的新命令或多重文件介面 \(MDI\) \(MDI\) 視窗新命令\)。  
  
 必須宣告 `CFrameWnd` 從取得的框架視窗類別與 `DECLARE_DYNCREATE` 為了頂端 `RUNTIME_CLASS` 機制以正確地運作。  
  
 在 \[ `CFrameWnd` 視窗的一般應用程式中包含預設實作會執行主視窗的下列功能:  
  
-   `CFrameWnd` 框架視窗記錄視窗是使用中視窗或目前輸入焦點的獨立的目前使用中的檢視。  當框架重新啟動時，現用檢視藉由呼叫 `CView::OnActivateView`告知。  
  
-   命令訊息和許多通用架構通知訊息，包含 `OnSetFocus`處理的組態， `OnHScroll`和 `CWnd`的 `OnVScroll` 函式而言，是一 `CFrameWnd` 框架視窗委派至目前使用中的檢視。  
  
-   目前作用中檢視 \(或在 MDI 架構情況下的目前作用中的 MDI 子框架視窗\) 可以判斷框架視窗的標題。  這項功能可以透過關閉框架視窗的 **FWS\_ADDTOTITLE** 樣式位元停用。  
  
-   `CFrameWnd` 框架視窗處理將控制列、檢視和其他子視窗在框架視窗的工作區中。  框架視窗也會進行閒置時間更新工具列和其他控制項的按鈕。  `CFrameWnd` 框架視窗也有一個命令的預設實作來切換按鈕的這個工具列和狀態列。  
  
-   `CFrameWnd` 框架視窗處理主功能表列。  當快顯功能表時，框架視窗使用 **UPDATE\_COMMAND\_UI** 機制來判斷應該啟用、停用，或是檢查哪些功能表項目。  當使用者選取功能表項目時，框架視窗更新訊息字串的狀態列該命令的。  
  
-   `CFrameWnd` 框架視窗會自動轉譯鍵盤快速鍵的選擇性快速鍵對應表。  
  
-   `CFrameWnd` 框架視窗會對即時線上說明使用的選擇性說明 ID 設定為 `LoadFrame` 。  框架視窗是 semimodal 狀態的主要管弦開放式小組例如即時線上說明 \(SHIFT\+F1\) 和預覽列印模式。  
  
-   `CFrameWnd` 框架視窗將會開啟在框架視窗拖曳檔案管理員和置放檔案。  如果副檔名並使向應用程式註冊，框架視窗回答發生的動態資料交換 \(DDE\) \(DDE\) 開放式需求，則當使用者開啟文件管理員的資料檔案，或是 **ShellExecute** Windows 函式呼叫時。  
  
-   如果框架視窗是主應用程式視窗 \( `CWinThread::m_pMainWnd`\)，也就是，當使用者關閉應用程式時，框架視窗會提示使用者儲存修改過的資料 \( `OnClose` 和 `OnQueryEndSession`\)。  
  
-   如果框架視窗是主應用程式視窗，框架視窗執行的 WinHelp 內容。  如果適用於這個應用程式，說明啟動關閉框架視窗都會關閉 WINHELP.EXE。  
  
 請不要使用 C\+\+ **刪除** 運算子終結框架視窗。  請改用 `CWnd::DestroyWindow`。  在終結， `PostNcDestroy` 的 `CFrameWnd` 實作要刪除 C\+\+ 物件視窗。  當使用者關閉框架視窗，預設 `OnClose` 管理員會呼叫 `DestroyWindow`。  
  
 如需 `CFrameWnd`的資訊，請參閱 [框架視窗](../../mfc/frame-windows.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd Class](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md)