---
title: "停駐和浮動工具列 | Microsoft Docs"
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
  - "CBRS_SIZE_DYNAMIC"
  - "CBRS_SIZE_FIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBRS_ALIGN_ANY 常數"
  - "CBRS_SIZE_DYNAMIC 常數"
  - "CBRS_SIZE_FIXED 常數"
  - "固定大小的工具列"
  - "浮動調色盤"
  - "浮動工具列"
  - "框架視窗, 工具列停駐"
  - "調色盤, 浮動"
  - "大小"
  - "大小, 工具列"
  - "工具列控制項 [MFC], 包裝"
  - "工具列 [C++], 停駐"
  - "工具列 [C++], 浮動"
  - "工具列 [C++], 大小"
  - "工具列 [C++], 包裝"
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 停駐和浮動工具列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫支援可停駐工具列。  可停駐工具列可以附加，或者停駐，與其父視窗的任何一邊或其小型框架視窗可以中斷連結或浮動，。  本文將您的應用程式會示範如何使用可停駐工具列。  
  
 如果您使用應用程式精靈產生應用程式的基本架構，要求您選取要停駐工具列。  根據預設，應用程式精靈會在您的應用程式執行必要三次的動作將可停駐工具列的程式碼:  
  
-   [啟用在框架視窗停駐](#_core_enabling_docking_in_a_frame_window)。  
  
-   [啟用工具列停駐](#_core_enabling_docking_for_a_toolbar)。  
  
-   [停駐工具列 \(到框架視窗\)](#_core_docking_the_toolbar)。  
  
 如果這些步驟的任何一個遺失，您的應用程式會顯示標準的工具列。  您一定要替程式中每一個可停駐工具列執行後兩個步驟。  
  
 在此文件中包含的其他主題:  
  
-   [浮動工具列](#_core_floating_the_toolbar)  
  
-   [動態調整大小的工具列](#_core_dynamically_resizing_the_toolbar)  
  
-   [設定內建樣式的工具列的包裝位置](#_core_setting_wrap_positions_for_a_fixed.2d.style_toolbar)  
  
 如需範例為一般 MFC [DOCKTOOL](../top/visual-cpp-samples.md) 範例。  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> 啟用在框架視窗停駐  
 若要停駐工具列加入至框架視窗，必須啟用框架視窗 \(或目標\) 允許固定。  使用 [CFrameWnd::EnableDocking](../Topic/CFrameWnd::EnableDocking.md) 函式，如此一來，採用 `DWORD` 參數是一組樣式位元表示框架視窗的哪一邊接受停駐。  如果工具列會固定，並且多邊它可以停駐，在參數中所指示的邊傳遞至 `EnableDocking` 以下列順序:上面，下方，保持，無效。  如果您想要將控制列停駐在任何位置，請將 `CBRS_ALIGN_ANY` 設定為 `EnableDocking`。  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> 啟用工具列停駐  
 在目的為固定準備後，您必須以相同的方式準備工具列 \(或來源\)。  您要停駐的每個工具列上呼叫 [CControlBar::EnableDocking](../Topic/CControlBar::EnableDocking.md) ，指定工具列應該固定的目的端。  如果在呼叫指定邊都與 `CControlBar::EnableDocking` 相符的讓 Pin 在框架視窗，工具列無法修正—它會浮動。  一旦浮動的話，工具列將永遠是浮動狀態，無法停駐在框架視窗上。  
  
 如果您要的作用是永久浮動工具列，呼叫具有參數的 `EnableDocking` 0。  接著會呼叫 [CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md)。  工具列保持浮動，永久無法任何位置固定。  
  
##  <a name="_core_docking_the_toolbar"></a> 固定工具列  
 架構會呼叫 [CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md) ，當使用者嘗試放入允許固定框架視窗的右邊的工具列。  
  
 此外，您可以隨時呼叫這個函式停駐控制列到框架視窗。  這在初始化時通常是。  多個工具列可以停駐在框架視窗的特定一邊。  
  
##  <a name="_core_floating_the_toolbar"></a> 浮動工具列  
 中斷連結框架視窗的停駐工具列呼叫浮動工具列。  呼叫執行此動作的 [CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md) 。  指定工具列會浮動的，它應該放置點和識別的對齊樣式浮點數工具列是否為水平或垂直。  
  
 架構會呼叫這個函式，當使用者拖曳工具列其停駐位置和置放在固定未啟用的位置時。  這可以是任何或框架視窗外內。  使用 `DockControlBar`，您可以在初始化時也會呼叫這個函式。  
  
 可停駐工具列的 MFC 實作不提供在支援可停駐工具列的某些應用程式中的某些擴充功能。  例如自訂的工具列不會提供功能。  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> 動態調整大小的工具列  
 根據 Visual C\+\+ 4.0 版，您可以使它成為可為您的應用程式的使用者動態調整浮動工具列。  通常，工具列具有長，線性圖案，水平顯示。  但是，您可以變更工具列的方向和它的圖案。  例如，在中，當使用者停駐工具列物件的其中一個框架視窗的垂直框，圖案變更為垂直配置。  變更工具列按鈕將有多行的矩形也是可能的。  
  
 您可以：  
  
-   指定動態調整大小做為工具列特性。  
  
-   指定固定大小做為工具列特性。  
  
 若要提供這項支援，有兩個新的工具列樣式用於呼叫 [CToolBar::Create](../Topic/CToolBar::Create.md) 成員函式。  這些視窗是：  
  
-   **CBRS\_SIZE\_DYNAMIC** 控制列是動態的。  
  
-   **CBRS\_SIZE\_FIXED** 控制列是固定的。  
  
 大小動態樣式讓使用者調整大小的工具列，當它浮動時，不過，沒有，當它停駐時。  工具列包裝」\(視需要變更形狀做為使用者拖曳其右邊緣。  
  
 大小固定的樣式保留工具列的包裝狀態，固定按鈕的位置在每個資料行。  您的應用程式的使用者無法變更工具列的圖案。  在指定的位置的工具列換行，例如分隔符號的位置在按鈕之間的。  它會保留此圖形工具列是否固定或浮動。  結果是有按鈕多行的固定的調色盤。  
  
 您也可以使用 [CToolBar::GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md) 傳回一個狀態和樣式按鈕在您的工具列。  按鈕的樣式決定按鈕的外觀，以及如何回應使用者輸入;這個狀態分辨按鈕是否顯示在包裝的狀態。  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed.2d.style_toolbar"></a> 設定內建樣式的工具列的包裝位置  
 如果有固定大小的樣式的工具列，指定的工具列按鈕的工具列會自動換行。  下列程式碼顯示如何針對在主框架視窗的 `OnCreate` 覆寫:  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/CPP/docking-and-floating-toolbars_1.cpp)]  
  
 一般 MFC [DOCKTOOL](../top/visual-cpp-samples.md) 範例示範如何使用 [CControlBar](../mfc/reference/ccontrolbar-class.md) 和 [CToolBar](../mfc/reference/ctoolbar-class.md) 類別的成員函式處理工具列的動態配置。  請參閱在 DOCKTOOL 的檔案 EDITBAR.CPP。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [工具列基本概念](../mfc/toolbar-fundamentals.md)  
  
-   [工具列工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
## 請參閱  
 [MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)