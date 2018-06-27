---
title: TN021： 命令和訊息路由 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.routing
dev_langs:
- C++
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22fcb3f9815e5100251e6bf478c6714fbb0b7df3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955718"
---
# <a name="tn021-command-and-message-routing"></a>TN021：命令和訊息路由
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示描述命令路由和分派架構，以及一般視窗訊息路由中的進階的主題。  
  
 請參閱 Visual c + + 的一般詳細資料，在此處描述的架構上特別區分 Windows 訊息、 控制通知和命令。 這個附註會假設您很熟悉列印文件中所述的問題，並僅解決非常進階的主題。  
  
## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>命令傳送和分派 MFC 1.0 發展至 MFC 2.0 的功能架構  
 Windows 具有多載之後可提供通知的功能表命令、 快速鍵和對話方塊控制項告知的 WM_COMMAND 訊息。  
  
 MFC 1.0 的有點藉由使用命令處理常式 (例如，"OnFileNew") 內建`CWnd`衍生類別呼叫以回應特定的 WM_COMMAND。 黏附以及稱為訊息對應的資料結構，並導致空間非常有效率的命令機制。  
  
 MFC 1.0 也會提供額外的功能，來分隔命令訊息的通知控制項。 命令會以 16 位元識別碼，有時也稱為命令識別碼。 正常啟動命令`CFrameWnd`（也就是功能表中選取或翻譯的 accelerator） 取得路由傳送至各種不同的 其他視窗。  
  
 MFC 1.0 會使用命令傳送有限的意義上，針對多重文件介面 (MDI) 的實作。 （MDI 框架視窗會委派其作用中的 MDI 子視窗的命令）。  
  
 這項功能已一般化並擴充 MFC 2.0 允許由較大範圍的物件 （不只是視窗物件） 來處理命令。 它提供更多型，並且可延伸的架構，以路由訊息，並重複使用的命令目標路由，不只會處理命令，但以反映目前可用的命令更新 UI 物件 （例如功能表項目和工具列按鈕）.  
  
## <a name="command-ids"></a>命令 ID  
 如需命令路由，並繫結程序的說明，請參閱 Visual c + +。 [技術提示 20](../mfc/tn020-id-naming-and-numbering-conventions.md)包含識別碼命名的相關資訊。  
  
 我們使用泛型的前置詞"ID_"命令識別碼。 命令 Id 是 > = 0x8000。 訊息列或狀態列會顯示命令的說明字串是否有 STRINGTABLE 資源具有相同識別碼為命令識別碼。  
  
 在應用程式的資源，可以 ID 的命令會出現在幾個地方：  
  
-   在一個 STRINGTABLE 資源具有相同的識別碼在訊息列提示字元。  
  
-   可能是許多功能表資源中附加至叫用在同一個命令的功能表項目。  
  
-   （進階） 對話方塊按鈕 GOSUB 命令中。  
  
 在您的應用程式的原始程式碼，的命令識別碼可以出現在幾個地方：  
  
-   在您的資源。H （或其他主要的符號標頭檔） 來定義特定應用程式的命令 Id。  
  
-   也許在用於建立工具列的識別碼陣列。  
  
-   ON_COMMAND 巨集。  
  
-   也許在 ON_UPDATE_COMMAND_UI 巨集。  
  
 目前，只有在需要的命令 Id 的 MFC 實作是 > = 0x8000 是 GOSUB 對話方塊/命令的實作。  
  
## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>使用對話方塊中的命令架構的 GOSUB 命令  
 路由及啟用命令的命令架構適用於框架視窗、 功能表項目、 工具列按鈕、 對話方塊列按鈕、 其他控制項列和設計用來更新指定和路由的命令或控制項 Id 加入至 main 其他使用者介面項目命令目標 （通常是主框架視窗）。 主要的命令目標可能會視其他命令目標物件路由命令或控制項通知。  
  
 對話方塊 （強制或非強制回應） 可以受益於某些命令架構的功能如果您將對話方塊控制項的控制項 ID 指派給適當的命令 id。 支援對話方塊不會自動，因此您可能必須撰寫額外的程式碼。  
  
 請注意，讓所有這些功能才能正常運作，您的命令 Id 應該是 > = 0x8000。 因為許多對話方塊可能會路由至相同的框架，共用的命令應該 > = 0x8000，而非共用的 IDCs 特定對話中應該是 < = 0x7FFF。  
  
 您可以在一般的強制回應對話方塊，設定為適當的命令 id。 按鈕的外觀與一般按鈕 當使用者選取按鈕時，對話方塊 （通常是主框架視窗） 的擁有者會取得命令，就像任何其他命令一樣。 這就稱為 GOSUB 命令，因為它通常用來顯示其他對話方塊 (GOSUB 的第一個對話方塊)。  
  
 您也可以呼叫此函式`CWnd::UpdateDialogControls`上您的對話方塊，並將它傳遞的主框架視窗的位址。 此函式將會啟用或停用您根據它們是否有命令處理常式之框架中的對話方塊控制項。 呼叫此函式會自動為您的控制列在您的應用程式閒置迴圈中，但您必須針對您想要讓這項功能的標準對話方塊直接呼叫它。  
  
## <a name="when-onupdatecommandui-is-called"></a>ON_UPDATE_COMMAND_UI 呼叫時  
 維持啟用/核取狀態的所有程式的功能表項目可以是高度耗費計算能力的問題。 啟用/核取功能表項目只在使用者選取快顯視窗時，才是常用的技巧。 MFC 2.0 實作`CFrameWnd`WM_INITMENUPOPUP 訊息的處理，並使用命令路由架構決定功能表透過 ON_UPDATE_COMMAND_UI 處理常式的狀態。  
  
 `CFrameWnd` 也可以處理 WM_ENTERIDLE 訊息來描述目前功能表項目選取狀態列的 （也稱為訊息列）。  
  
 Visual c + + 中，編輯的應用程式功能表結構用來代表潛在的命令適用於 WM_INITMENUPOPUP 階段。 ON_UPDATE_COMMAND_UI 處理常式可以修改的狀態或文字的功能表，或供進階使用 （檔案 MRU 清單或 OLE 動詞命令的快顯功能表），實際修改功能表結構功能表繪製前。  
  
 ON_UPDATE_COMMAND_UI 處理的相同排序基於工具列 （和其他控制項列） 應用程式時進入其閒置迴圈。 請參閱*類別庫參考*和[技術提示 31](../mfc/tn031-control-bars.md)如需有關控制列。  
  
## <a name="nested-pop-up-menus"></a>巢狀快顯功能表  
 如果您使用巢狀的功能表結構，您會發現快顯功能表中的第一個功能表項目 ON_UPDATE_COMMAND_UI 處理常式會在兩個不同的情況下呼叫。  
  
 首先，它是針對快顯功能表本身呼叫。 這是必要的因為快顯功能表中沒有識別碼，我們使用的快顯功能表的第一個功能表項目識別碼來參考整個快顯功能表。 在此情況下， *m_pSubMenu*成員變數`CCmdUI`物件會為非 NULL，將會為快顯功能表。  
  
 第二，它稱為之前所要繪製的快顯功能表中的功能表項目。 在此情況下，識別碼是指只第一個功能表項目和*m_pSubMenu*成員變數`CCmdUI`物件會是 NULL。  
  
 這可讓您啟用快顯功能表不同於其功能表項目，但您必須撰寫一些功能表感知程式碼。 例如，在具有下列結構的巢狀功能表：  
  
```  
File>  
    New> 
    Sheet (ID_NEW_SHEET)  
    Chart (ID_NEW_CHART)  
```  
  
 ID_NEW_SHEET 和 ID_NEW_CHART 命令可以個別啟用或停用。 **新增**應該啟用快顯功能表上，如果上述兩個已啟用。  
  
 ID_NEW_SHEET （快顯視窗中的第一個命令） 的命令處理常式會看起來像：  
  
```  
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)  
{  
    if (pCmdUI->m_pSubMenu != NULL)  
 { *// enable entire pop-up for "New" sheet and chart  
    BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;  
 *// CCmdUI::Enable is a no-op for this case,
    so we *//   must do what it would have done.  
    pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex, 
    MF_BYPOSITION |   
 (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

    return; 
 } *// otherwise just the New Sheet command  
    pCmdUI->Enable(m_bCanCreateSheet);

} 
```  
  
 ID_NEW_CHART 的命令處理常式會是一般更新命令處理常式，而且類似的外觀：  
  
```  
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)  
{  
    pCmdUI->Enable(m_bCanCreateChart);

} 
```  
  
## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND 和 ON_BN_CLICKED  
 訊息對應巨集，如**ON_COMMAND**和**ON_BN_CLICKED**都相同。 MFC 命令和控制通知路由機制只會使用命令識別碼決定路由傳送至的位置。 控制與控制項通知碼為零的通知 (**BN_CLICKED**) 解譯為命令。  
  
> [!NOTE]
>  事實上，所有的控制項通知訊息會通過命令處理常式鏈結。 比方說，是您可以撰寫控制項告知處理常式的可行**EN_CHANGE**文件類別中。 這是功能的不通常建議，因為很少，這項功能的實際應用、 ClassWizard，不支援的功能和使用可能會導致易損壞的程式碼。  
  
## <a name="disabling-the-automatic-disabling-of-button-controls"></a>停用自動停用功能的按鈕控制項  
 如果您將對話方塊列上的按鈕控制項，或使用 where 對話方塊中您要呼叫**CWnd::UpdateDialogControls**自己，您會注意到該按鈕，並沒有**ON_COMMAND**或**ON_UPDATE_COMMAND_UI**處理常式會自動停用您的架構。 在某些情況下，您不需要有處理常式，但您會想要持續啟用按鈕。 為了達到這個目的最簡單的方式是加入空的命令處理常式 （簡單與 ClassWizard） 和不在其中執行任何動作。  
  
## <a name="window-message-routing"></a>視窗訊息路由  
 以下說明一些更進階的主題上的 MFC 類別，以及它們如何影響 Windows 訊息路由和其他的主題。 這裡的資訊僅簡單描述。 請參閱*類別庫參考*公用 Api 的詳細資料。 請參閱 MFC 程式庫原始程式碼，如需有關實作詳細資料。  
  
 請參閱[技術附註 17](../mfc/tn017-destroying-window-objects.md)視窗清除的詳細資訊，非常重要的主題，適用於所有**CWnd**-衍生的類別。  
  
## <a name="cwnd-issues"></a>CWnd 問題  
 實作成員函式**On_xxx_reflect**提供功能強大且可延伸的架構，來攔截 (hook) 或否則通知的訊息、 命令和控制項的子視窗 （也就是控制項）請移至其父代 （或 「 擁有者 」） 的通知。 如果子視窗 （/ 控制） 是 c + + **CWnd**物件本身，虛擬函式**OnChildNotify**會先呼叫具有參數從原始訊息 (也就是**MSG**結構)。 子視窗可以保留訊息、 吃，或修改訊息的父代 （罕見）。  
  
 預設值**CWnd**實作會處理下列兩則訊息，並使用**OnChildNotify**允許子視窗 （控制項） 至第一次存取位置的訊息勾點：  
  
- **WM_MEASUREITEM**和**WM_DRAWITEM** （的自繪）  
  
- **WM_COMPAREITEM**和**WM_DELETEITEM** （的自繪）  
  
- **WM_HSCROLL**和**WM_VSCROLL**  
  
- **WM_CTLCOLOR**  
  
- **WM_PARENTNOTIFY**  
  
 您會注意到**OnChildNotify**攔截程序用來變更主控描繪訊息至自繪訊息。  
  
 除了**OnChildNotify**攔截，捲動訊息有進一步的路由行為。 請參閱下方的捲軸和來源的詳細**WM_HSCROLL**和**WM_VSCROLL**訊息。  
  
## <a name="cframewnd-issues"></a>CFrameWnd 問題  
 **CFrameWnd**類別提供的大部分命令路由和使用者介面更新的實作。 這主要做為應用程式的主框架視窗 (**M_pmainwnd**)，但適用於所有框架視窗。  
  
 主框架視窗是功能表列的視窗和 [狀態] 列的父系或訊息列。 請參閱上述的討論內容，在命令路由和**WM_INITMENUPOPUP。**  
  
 **CFrameWnd**類別提供管理功能的作用中的檢視。 透過使用中的檢視，進行路由傳送下列訊息：  
  
-   （使用中的檢視會取得它們的第一次存取） 的所有命令訊息。  
  
- **WM_HSCROLL**和**WM_VSCROLL**訊息從同層級捲軸 （請參閱下文）。  
  
- **WM_ACTIVATE** (和**WM_MDIACTIVATE** mdi) 的虛擬函式呼叫取得變成**CView::OnActivateView**。  
  
## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd 問題  
 這兩個 MDI 框架視窗類別衍生自**CFrameWnd**和同時啟用的相同類型的命令路由，因此使用者介面更新中提供和**CFrameWnd**。 在典型 MDI 應用程式中，只有主框架視窗 (也就是**CMDIFrameWnd**物件) 會保存在功能表列和狀態列，因此命令路由實作的主要來源。  
  
 一般路由配置是現用的 MDI 子視窗取得命令的第一次存取。 預設值**PreTranslateMessage**函式中處理這兩個 MDI 子視窗的快速鍵對應表 （第一次） 和 MDI 框架 （第二個） 以及通常由標準 MDI 系統命令快速鍵**TranslateMDISysAccel** （最後一個）。  
  
## <a name="scroll-bar-issues"></a>捲軸的問題  
 當處理捲動訊息 (**WM_HSCROLL**/**OnHScroll**及/或**WM_VSCROLL**/**OnVScroll**)，您應該嘗試寫入處理常式程式碼，因此它不會依賴捲軸列訊息的來源。 這不只是一般的 Windows 問題，因為捲動訊息可能來自 true 捲軸控制項，或從**WS_HSCROLL**/**WS_VSCROLL**捲軸不是捲軸控制項。  
  
 MFC 擴充，讓子系或同層級正在捲動視窗的捲軸控制項 （事實上，捲軸和要捲動的視窗之間的父子式關聯性可以是任何項目）。 這是共用的捲軸，以分隔視窗尤其重要。 請參閱[技術附註 29](../mfc/tn029-splitter-windows.md)如需詳細資訊的實作**CSplitterWnd**包括的詳細資訊，在共用的捲軸列問題。  
  
 上附帶一提，有兩個**CWnd**衍生的類別，在指定的捲軸樣式建立時間是截取，不會傳送到 Windows。 當傳遞給建立常式**WS_HSCROLL**和**WS_VSCROLL**可以獨立設定，但無法變更建立之後。 當然，您應該不會直接測試，或設定 WS_SCROLL 樣式位元，他們所建立的視窗。  
  
 如**CMDIFrameWnd**捲軸樣式您傳遞給**建立**或**LoadFrame**用來建立 MDICLIENT。 如果您想要擁有的是可捲動的 MDICLIENT 區域 （例如 Windows 程式經理） 務必設定兩者捲軸樣式 (**WS_HSCROLL** &#124; **WS_VSCROLL**) 用來建立樣式**CMDIFrameWnd**。  
  
 如**CSplitterWnd**捲軸樣式套用至分割區的特殊共用的捲軸。 靜態分隔視窗，您通常不會設定任一捲軸列樣式。 動態分隔視窗，您通常會有捲軸的方向，您將分割，也就是樣式設定**WS_HSCROLL**是否可以將資料列， **WS_VSCROLL**是否可以將資料行。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

