---
title: "TN021：命令和訊息路由 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.routing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令傳送 [C++], 技術提示 TN021"
  - "TN021"
  - "Windows 訊息 [C++], 傳送"
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN021：命令和訊息路由
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個附註在一般 Windows 訊息路由描述命令路由和分派結構以及進階主題。  
  
 如需 Visual C\+\+ 有關在此處，特別是所描述之結構的一般詳細資料視窗訊息之間的差異，控制通知和命令。  這個附註假設您熟悉徹底只列印的文件和位址非常進階主題所述的問題。  
  
## 命令路由和分派 MFC 1.0 功能進展到 MFC 2.0 結構  
 視窗有多載提供命令、快速鍵和對話方塊控制項通知告知的 **WM\_COMMAND** 訊息。  
  
 在該 1.0 建置 MFC 一點可讓命令處理常式 \(例如， 「OnFileNew」\) 在 **CWnd** 衍生類別呼叫以回應特定 **WM\_COMMAND**。  這相當於一個非常空間有效的命令機制的資料結構稱為訊息對應的和結果一起膠組合。  
  
 中斷連接的控制項告知 MFC 1.0 也提供額外的功能從命令訊息。  命令由 16 位元 ID 代表，有時稱為命令 ID.  命令從 **CFrameWnd** \(也就是選取的功能表或其他轉譯的快速鍵\) 通常會啟動並會路由至各種其他視窗。  
  
 在有限的意義的 MFC 1.0 中使用命令傳送多重文件介面 \(MDI\) \(MDI\) 實作。\(MDI 框架視窗委派至其作用中的 MDI 子視窗\)。  
  
 這項功能在 MFC 2.0 推斷並擴充允許命令由各種物件 \(而不只是視窗物件\) 來處理。  它會將訊息傳送到更正式的結構和重複使用不僅處理的命令目標路由命令，，而且為更新 UI 物件 \(例如功能表項目和工具列按鈕\) 以命令目前的可用性。  
  
## 命令 ID。  
 為命令路由和繫結處理序的說明參閱 Visual C\+\+。  如需[Technical Note 20](../mfc/tn020-id-naming-and-numbering-conventions.md) ID 命名的相關資訊。  
  
 我們為命令 ID 使用泛型前置詞「ID\_」。  命令 ID 是 \>\= 0x8000。  如果具有 ID 的 STRINGTABLE 資源和訂單 ID. 相同，這個訊息列或狀態列會顯示命令描述字串  
  
 在您的應用程式資源，命令 ID 可以於數個出現:  
  
-   在具有 ID 和訊息行提示相同 STRINGTABLE 資源。  
  
-   在可以附加至功能表項目叫用相同的命令的功能表資源。  
  
-   \(進階\)。GOSUB 命令的一個對話方塊按鈕。  
  
 在您的應用程式原始程式碼，命令 ID 可以於數個出現:  
  
-   在您的\) 定義應用程式特定的命令 ID 的 RESOURCE.H \(或其他主要符號標頭檔。  
  
-   可能在使用的 ID 陣列建立工具列。  
  
-   在 **ON\_COMMAND** 巨集。  
  
-   可能在 **ON\_UPDATE\_COMMAND\_UI** 巨集。  
  
 目前，要求命令 ID 在 MFC 的唯一實作為 \= \>0x8000 是 GOSUB 對話\/命令的實作。  
  
## GOSUB 命令，使用對話的命令結構  
 路由命令結構和啟用命令很好與框架視窗，功能表項目，工具列按鈕，對話方塊列一起使用的，其設計的其他控制項的資料行和其他使用者介面項目更新隨選和路由命令或控制項 ID 加入至主命令目標 \(通常主框架視窗\)。  主命令目標可以傳送命令或控制項通知給其他命令中目標物件屬性。  
  
 對話方塊 \(強制回應或非強制回應\) 可能會因某些命令結構的功能，將對話方塊控制項的控制項 ID 為適當的命令 ID.  支援對話方塊不是自動的，因此，您必須撰寫一些額外的程式碼。  
  
 請注意對於這些功能可以正常運作，您的命令 ID 應該是 \>\= 0x8000。  因為許多對話方塊可能會路由到相同框架，共用命令應該是 \>\= 0x8000，，而在特定對話方塊的非共用 IDCs 應該是 \<\= 0x7FFF。  
  
 您可以使用按鈕的 IDC 的一般強制回應對話方塊可以將一般按鈕設定為適當的命令 ID.  當使用者選取按鈕時，對話方塊 \(通常主框架視窗\) 的擁有者取得命令與其他命令。  這個呼叫 GOSUB 命令，因為它通常用來引發另一個對話方塊 \(第一個對話方塊的 GOSUB\)。  
  
 您也可以呼叫在對話方塊的函式 **CWnd::UpdateDialogControls** 和將您的主框架視窗位址。  這個函式會啟用或停用您的架構的對話方塊控制項是否有命令處理常式在框架。  這個函式會自動呼叫您的應用程式閒置迴圈的控制列的，不過，您必須呼叫它直接一般對話方塊上要有這項功能。  
  
## 當 ON\_UPDATE\_COMMAND\_UI 呼叫  
 維護允許\/核取狀態所有程式的功能表項目可以一直是一個計算高度耗費資源的問題。  只有在使用者選取快顯功能表時，一個常用的技巧是啟用\/檢查功能表項目。  **CFrameWnd** 的 MFC 2.0 實作處理 **WM\_INITMENUPOPUP** 訊息並使用命令路由結構傳遞 **ON\_UPDATE\_COMMAND\_UI** 處理常式判斷功能表狀態。  
  
 **CFrameWnd** 也處理 **WM\_ENTERIDLE** 訊息描述在狀態列目前選取的功能表項目 \(也稱為訊息行\)。  
  
 應用程式的功能表結構，編輯由 Visual C\+\+，用來代表可能的可用命令。 **WM\_INITMENUPOPUP** 時間。  **ON\_UPDATE\_COMMAND\_UI** 處理常式可以修改功能表狀態或文字，或針對進階使用方式 \(如檔案 MRU 清單或 OLE 動詞快顯功能表\)，實際修改功能表結構，在繪製前功能表。  
  
 同一個 **ON\_UPDATE\_COMMAND\_UI** 處理為工具列 \(和其他控制項列\) 完成，當應用程式進入其閒置迴圈時。  請參閱 *類別庫參考* 和 [Technical Note 31](../mfc/tn031-control-bars.md) 有關控制列的詳細資訊。  
  
## 巢狀快顯功能表  
 如果您使用巢狀功能表結構，您會注意到第一個功能表項目的 **ON\_UPDATE\_COMMAND\_UI** 處理常式在快顯功能表在兩個不同情況下呼叫。  
  
 首先，它為快顯功能表時呼叫。  這是必要的，因為快顯功能表沒有 ID，我們使用快顯功能表的第一個功能表項目的 ID 參考整個快顯功能表。  在這種情況下， **CCmdUI** 物件的 **m\_pSubMenu** 成員變數為非 null，並指向快顯功能表。  
  
 其次，，在繪製之前，它會在快顯功能表的功能表項目。  在這種情況下， ID 參考第一個功能表項目，並 **CCmdUI** 物件的 **m\_pSubMenu** 成員變數是空的。  
  
 這可讓您啟用快顯功能表區別其功能表項目，不過，您必須撰寫一些功能表明確的程式碼。  例如，在具有下列結構的巢狀功能表:  
  
```  
File>  
    New>  
        Sheet (ID_NEW_SHEET)  
        Chart (ID_NEW_CHART)  
```  
  
 ID\_NEW\_SHEET 和 ID\_NEW\_CHART 命令都可以單獨啟用或停用。  **New** 快顯功能表，如果其中一個或兩個已啟用，應該啟用。  
  
 ID\_NEW\_SHEET \(在快顯的第一個命令的命令處理常式\) 會看起來會像這樣:  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
    {  
        // enable entire pop-up for "New" sheet and chart  
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
  
        // CCmdUI::Enable is a no-op for this case, so we  
        //   must do what it would have done.  
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,  
            MF_BYPOSITION |   
                (bEnable ? MF_ENABLED : (MF_DISABLED | MF_GRAYED)));  
        return;  
    }  
    // otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);  
}  
```  
  
 ID\_NEW\_CHART 的命令處理常式會正常更新命令處理常式和外觀類似:  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);  
}  
```  
  
## ON\_COMMAND 和 ON\_BN\_CLICKED  
 **ON\_COMMAND** 和 **ON\_BN\_CLICKED** 的訊息對應巨集相同。  MFC 命令和控制項通知路由機制在何處只使用命令 ID 決定傳送。  控制項與控制項通知程式碼的通知零 \(**BN\_CLICKED**\) 解譯為命令。  
  
> [!NOTE]
>  事實上，所有控制項通知訊息通過命令處理常式鏈結。  例如，將控制項告知處理常式為 **EN\_CHANGE** 在文件類別您在技術上是可行的。  這通常不是可執行的，因為這個功能的實際應用是較少，功能不會由 ClassWizard 支援，因此，對功能可能會導致損壞的程式碼。  
  
## 停用按鈕控制項自動停用  
 如果您將按鈕控制項在一個對話方塊，或在自己的呼叫 **CWnd::UpdateDialogControls** 的對話方塊使用時，您會注意到未 **ON\_COMMAND** 和 **ON\_UPDATE\_COMMAND\_UI** 處理常式的按鈕將會自動停用由架構。  在某些情況下，您不需要有處理常式，不過，您要將按鈕保持啟用。  最簡單的方式達成這項作業會將假的命令處理常式 \(可利用 ClassWizard\) 並不會使用它。  
  
## 視窗訊息路由  
 下列說明 MFC 類別的某些進階主題，而 Windows 訊息路由和其他主題如何影響它們。  此資訊簡單地只說明。  如需公用 API 的詳細資訊，請參閱 *類別庫參考* 。  請參閱 MFC 程式庫原始程式碼與執行詳細資料的詳細資訊。  
  
 請參閱 [Technical Note 17](../mfc/tn017-destroying-window-objects.md) 相對於視窗清除的詳細資料，所有 **CWnd**中非常重要主題衍生類別。  
  
## CWnd 問題  
 實作成員函式 **CWnd::OnChildNotify** 為子視窗 \(也稱為控制項\) 提供強大結構給攔截或會通知訊息、命令和移至其父代的控制項告知 \(或擁有人\)。  如果子視窗 \(\/control 是 C \+\+. **CWnd** 物件，虛擬函式 **OnChildNotify** 首先呼叫與這個原始訊息 \(即 **MSG** 結構\) 的參數。  子視窗不會處理訊息，要求您提供它或修改父的訊息 \(不常見\)。  
  
 預設 **CWnd** 實作處理下列資訊並使用 **OnChildNotify** 攔截允許子視窗 \(控制項\) 加入至第一個元件的訊息:  
  
-   **WM\_MEASUREITEM** 和 **WM\_DRAWITEM** \(為自繪製\)  
  
-   **WM\_COMPAREITEM** 和 **WM\_DELETEITEM** \(為自繪製\)  
  
-   **WM\_HSCROLL** 和 **WM\_VSCROLL**  
  
-   **WM\_CTLCOLOR**  
  
-   **WM\_PARENTNOTIFY**  
  
 您會發現 **OnChildNotify** 攔截為變更主控描繪訊息使用自訂繪製訊息。  
  
 除了攔截 **OnChildNotify** 之外，捲動訊息有進一步路由行為。  如需詳細資訊請參閱以下在 **WM\_HSCROLL** 和 **WM\_VSCROLL** 訊息捲軸和來源。  
  
## CFrameWnd 問題  
 **CFrameWnd** 類別提供更新實作的大部分命令路由和使用者介面。  對於應用程式主要使用 \(**CWinApp::m\_pMainWnd**\) 的主框架視窗，但適用於所有框架視窗。  
  
 主框架視窗是有功能表列的視窗並為狀態列或訊息行的父代。  如需有關命令路由和 **WM\_INITMENUPOPUP.**的上述討論  
  
 **CFrameWnd** 類別提供現用檢視表的管理。  下列資訊將現用檢視路由:  
  
-   所有命令訊息 \(現用檢視取得其第一次存取\)。  
  
-   從同層級捲軸的**WM\_HSCROLL** 和 **WM\_VSCROLL** 訊息 \(參看下方\)。  
  
-   MDI 的 \(**WM\_ACTIVATE** 和 **WM\_MDIACTIVATE** \) get 會變成呼叫虛擬函式 **CView::OnActivateView**。  
  
## CMDIFrameWnd\/CMDIChildWnd 問題  
 兩個 MDI 框架視窗類別從 **CFrameWnd** 衍生也是相同類別的允許在 **CFrameWnd**和使用者介面更新提供的命令路由。  在典型的 MDI 應用程式，只有主框架視窗 \(即 **CMDIFrameWnd** 物件\) 保留功能表列和狀態列也是命令傳送實作的主要來源。  
  
 一般路由計劃是作用中的 MDI 子視窗取得命令的第一次存取。  預設 **PreTranslateMessage** 函式處理 MDI 子視窗的快速鍵對應表 \(先\) 和 MDI 框架 \(秒\) 以及 **TranslateMDISysAccel** 通常處理的標準 MDI 系統命令快速鍵 \(例如\)。  
  
## 捲軸問題  
 當處理捲動訊息 \(**WM\_HSCROLL**和**OnHScroll** 和 **WM\_VSCROLL**和**OnVScroll**\) 時，您應嘗試寫入處理常式程式碼，讓它與捲軸訊息來源。  這是除了一般視窗問題，，因為捲動訊息可以來自 true 捲軸控制項不是或捲軸控制項 **WS\_HSCROLL**和**WS\_VSCROLL** 捲軸。  
  
 允許的 MFC 擴充捲軸控制項移動視窗的子系或同層級 \(事實上，捲軸之間的父\/子移動的關聯性和視窗可以是任何\)。  這會以分隔視窗的捲軸時特別重要。  請參閱 [Technical Note 29](../mfc/tn029-splitter-windows.md) 。如需 **CSplitterWnd** 的實作詳細資料包含共用捲軸問題的詳細資訊。  
  
 在標記旁，有捲軸樣式會指定在建立時間被截取並不會傳遞給 Windows 的兩個 **CWnd** 衍生類別。  當傳遞至建立常式， **WS\_HSCROLL** 和 **WS\_VSCROLL** 可以獨立設定，不過，，則無法變更之後建立。  當然，您不應該直接測試或設定 WS\_? 移除它們建立視窗的樣式位元。  
  
 對於 **CMDIFrameWnd** 傳遞給 **Create** 的捲軸樣式或 **LoadFrame** 用來建立 MDICLIENT。  如果您希望有可捲動 MDICLIENT 區域 \(例如視窗項目管理員\) 請務必將兩個捲軸樣式 \(**WS\_HSCROLL** &#124; **WS\_VSCROLL**\) 所使用的樣式建立 **CMDIFrameWnd**。  
  
 對於 **CSplitterWnd** 捲軸樣式套用至共用特殊捲軸為分隔器區域。  對於靜態分隔視窗，您通常不會設定的任一個捲軸樣式。  對於動態分隔視窗，您通常會將捲軸樣式設定為您要分割的方向，也就是說，如果 **WS\_HSCROLL** ，您可以將資料行， **WS\_VSCROLL** ，則您可以將資料行。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)