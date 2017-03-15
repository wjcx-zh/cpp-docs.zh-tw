---
title: "MFC 工具列實作 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "點陣圖 [C++], 工具列"
  - "按鈕 [C++], MFC 工具列"
  - "CToolBar 類別, 建立工具列"
  - "CToolBarCtrl 類別, 實作工具列"
  - "停駐工具列"
  - "浮動工具列"
  - "MFC 工具列"
  - "工具提示 [C++], 啟用"
  - "工具列控制項 [MFC]"
  - "工具列 [C++]"
  - "工具列 [C++], 建立"
  - "工具列 [C++], 停駐"
  - "工具列 [C++], 浮動"
  - "工具列 [C++], 實作 MFC 工具列"
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC 工具列實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

工具列是包含控制項的點陣圖影像的 [控制列](../mfc/control-bars.md) 。  這些影像可能有行為，例如按鈕、核取方塊或選項按鈕。  MFC 提供類別處理工具列的 [CToolbar](../mfc/reference/ctoolbar-class.md) 。  
  
 如果您啟用它， MFC 工具列的使用者可以將它們停駐到視窗邊緣或任何位置在應用程式視窗內「浮動」它們。  MFC 不支援在某些開發環境下自訂的工具列。  
  
 MFC 也支援工具提示: 當您將滑鼠移到按鈕上時，會有小型快顯視窗描述工具列按鈕的目的。  根據預設，在中，當使用者按一下工具列按鈕狀態時，字串會出現在狀態列 \(如果有的話\)。  您可以啟動「Fly by」更新狀態，使得當滑鼠移過他的位置時，就會顯示目前更新狀態。  
  
> [!NOTE]
>  根據 MFC 4.0 版，工具列和工具提示中實作使用 Windows 95 \(含\) 以後版本的功能而不是目前實作特定對 MFC。  
  
 如需回溯相容性，在 MFC 類別 **COld工具列**保留舊的工具列實作。  MFC 舊版本的文件描述 `CToolBar`下的 **COld工具列**。  
  
 藉由選取應用程式精靈的工具列選項以建立程式的第一個工具列。  您也可以建立其他的工具列。  
  
 下列本文中引入:  
  
-   [工具列按鈕](#_core_toolbar_buttons)  
  
-   [停駐和浮動工具列](#_core_docking_and_floating_toolbars)  
  
-   [工具列和工具提示](#_core_toolbars_and_tool_tips)  
  
-   [CToolBar 和 CToolBarCtrl 類別](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [工具列點陣圖](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a> 工具列按鈕  
 工具列的按鈕類似於功能表項目。  兩種使用者介面物件皆會產生程式中的函式會處理的命令。  通常工具列按鈕重複選單的命令功能，提供使用者介面替代的相同功能。  這類重複的按鈕和功能具有相同的ID。  
  
 您可以在工具列的按鈕顯示和運作為按鈕、核取方塊或選項按鈕。  如需詳細資訊，請參閱 [CToolBar](../mfc/reference/ctoolbar-class.md) 類別。  
  
##  <a name="_core_docking_and_floating_toolbars"></a> 停駐和浮動工具列  
 MFC 工具列可以:  
  
-   靜止沿著其父視窗的一方。  
  
-   請依您指定父視窗的任何一邊或右邊的使用者拖曳和「停駐」，或者附加。  
  
-   請使框架視窗浮動，或中斷它的小型框架視窗連結，以便讓使用者移動到任何方便的位置。  
  
-   當浮動時請調整大小。  
  
 如需詳細資訊，請參閱文件 [固定或浮動工具列](../mfc/docking-and-floating-toolbars.md)。  
  
##  <a name="_core_toolbars_and_tool_tips"></a> 工具列和工具提示  
 MFC 工具列也會顯示「包含工具列按鈕的用途的簡短說明的工具提示」—微小的快顯視窗。  因為使用者移到工具列按鈕上方時，出現提供工具提示的視窗。  如需詳細資訊，請參閱文件 [工具列工具提示](../mfc/toolbar-tool-tips.md)。  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar 和 CToolBarCtrl 類別  
 您透過 [CToolBar](../mfc/reference/ctoolbar-class.md)類別來管理應用程式的工具列。  根據 MFC 4.0 版中， `CToolBar` 被實做為在 Windows 95 \(含\) 以後版本和 Windows NT 3.51 版下 \(含\) 以後版本皆可使用工具列通用控制項。  
  
 因為 MFC 使用作業系統的支援，所以 reimplementation 產生較少為工具列寫的 MFC 程式碼。  reimplementation 也加強功能。  您可以使用 `CToolBar` 成員函式操作工具列，也可以取得基底 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 物件的參考以及呼叫它的工具列自訂和其他功能的成員函式。  
  
> [!TIP]
>  如果您大量投入於 `CToolBar`的舊版 MFC 實作了，該支援仍可供使用。  請參閱本文件的 [使用舊的工具列](../mfc/using-your-old-toolbars.md)。  
  
 請參閱一般 MFC [DOCKTOOL](../top/visual-cpp-samples.md)範例。  
  
##  <a name="_core_the_toolbar_bitmap"></a> 工具列點陣圖  
 在建構完成後， `CToolBar` 物件透過載入單一的點陣圖建立工具列影像中每個按鈕的影像。  應用程式精靈建立您可以使用 Visual C\+\+自訂 [工具列編輯器](../mfc/toolbar-editor.md)的標準工具列的點陣圖。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [工具列基本概念](../mfc/toolbar-fundamentals.md)  
  
-   [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具列工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 類別  
  
## 請參閱  
 [工具列](../mfc/toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)