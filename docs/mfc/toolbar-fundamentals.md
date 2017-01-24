---
title: "工具列基本概念 | Microsoft Docs"
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
  - "RT_TOOLBAR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式精靈 [C++], 安裝預設應用程式工具列"
  - "命令 ID, 工具列按鈕"
  - "CToolBar 類別, 應用程式精靈中的預設工具列"
  - "將工具列內嵌於框架視窗類別中"
  - "框架視窗類別, 工具列內嵌於"
  - "LoadBitmap 方法, 工具列"
  - "LoadToolBar 方法"
  - "資源 [MFC], 工具列"
  - "RT_TOOLBAR 資源"
  - "SetButtons 方法"
  - "工具列控制項 [MFC], 命令 ID"
  - "工具列控制項 [MFC], 使用應用程式精靈建立的工具列"
  - "工具列編輯器, 應用程式精靈"
  - "工具列 [C++], 使用應用程式精靈加入預設的"
  - "工具列 [C++], 建立"
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 工具列基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明可讓您將預設工具列加入至您的應用程式可以選取應用程式精靈中選項的基本 MFC 實作。  涵蓋的主題包括：  
  
-   [應用程式精靈工具列索引標籤](#_core_the_appwizard_toolbar_option)  
  
-   [工具列的程式碼](#_core_the_toolbar_in_code)  
  
-   [編輯工具列資源](#_core_editing_the_toolbar_resource)  
  
-   [多個工具列](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a> 應用程式精靈工具列索引標籤  
 若要取得預設按鈕的單一工具列，請選取標記為使用者介面功能的網頁的標準停駐工具列選項。  這會將程式碼加入至應用程式的:  
  
-   建立工具列物件。  
  
-   處理工具列，包括其能力固定或浮動。  
  
##  <a name="_core_the_toolbar_in_code"></a> 工具列的程式碼  
 工具列是做為應用程式的 **CMainFrame** 類別的資料成員宣告的 [CToolBar](../mfc/reference/ctoolbar-class.md) 物件。  換句話說，工具列物件在主框架視窗物件中。  這表示 MFC 建立工具列，在建立框架視窗時會終結工具列，會終結框架視窗時。  下列部分類別宣告，多重文件介面 \(MDI\) \(MDI\) 應用程式中，顯示內嵌工具列和內嵌狀態欄位資料成員。  它同時也示範了 `OnCreate` 成員函式的覆寫。  
  
 [!code-cpp[NVC_MFCListView#6](../mfc/codesnippet/CPP/toolbar-fundamentals_1.h)]  
  
 工具列在 **CMainFrame::OnCreate**的建立隨即出現。  MFC 在建立框架視窗後呼叫 [OnCreate](../Topic/CWnd::OnCreate.md) ，但是，在它成為可見的。  應用程式精靈所產生的預設 `OnCreate` 工具列執行下列工作:  
  
1.  呼叫 `CToolBar` 物件的 [建立](../Topic/CToolBar::Create.md) 成員函式來建立基本的 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 物件。  
  
2.  呼叫 [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) 以載入工具列資源資訊。  
  
3.  呼叫函式啟用停駐，浮動和工具提示。  如需這些呼叫的詳細資訊，請參閱本文件的 [固定或浮動工具列](../mfc/docking-and-floating-toolbars.md)。  
  
> [!NOTE]
>  一般 MFC [DOCKTOOL](../top/visual-cpp-samples.md) 範例包括舊和新的 MFC 工具列的圖例。  使用 **COldToolbar** 的工具列要求呼叫步驟 2 對 `LoadBitmap` \(而不是 `LoadToolBar`\) 以及 `SetButtons`。  新的工具列要求呼叫 `LoadToolBar`。  
  
 停駐，浮動和工具提示呼叫是選擇性的。  如果有需要，您可以從 `OnCreate` 移除這些行。  結果是保持固定，無法浮動或 redock 和無法顯示工具提示的工具列。  
  
##  <a name="_core_editing_the_toolbar_resource"></a> 編輯工具列資源  
 取得與應用程式精靈的預設工具列根據 **RT\_TOOLBAR** 自訂資源，會在 MFC 4.0 版。  您可以編輯與 [工具列編輯器](../mfc/toolbar-editor.md)的這個資源。  編輯器可讓您輕鬆地加入，刪除和重新整理按鈕。  它包含非常類似於 Visual C\+\+ 的一般圖形編輯按鈕的圖形編輯器。  如果您編輯在舊版 Visual C\+\+ 中的工具列，您現在要尋找工作更容易。  
  
 若要連接工具列按鈕加入至命令，將按鈕命令 ID，例如 `ID_MYCOMMAND`。  指定命令 ID 在工具列編輯器中按鈕的屬性頁。  然後建立命令的處理常式函式 \(請參閱 [out 此函式之對應訊息](../mfc/reference/mapping-messages-to-functions.md) 以取得詳細資訊\)。  
  
 新的 [CToolBar](../mfc/reference/ctoolbar-class.md) 成員函式與 **RT\_TOOLBAR** 資源一起使用。  [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) 現在會取代 [LoadBitmap](../Topic/CToolBar::LoadBitmap.md) 載入工具列按鈕影像的點陣圖和 [SetButtons](../Topic/CToolBar::SetButtons.md) 將按鈕樣式和連接有點陣圖影像的按鈕。  
  
 如需使用工具列編輯器的詳細資訊，請參閱 [工具列編輯器](../mfc/toolbar-editor.md)。  
  
##  <a name="_core_multiple_toolbars"></a> 多個工具列  
 應用程式精靈可為您提供一個預設工具列。  如果您在您的應用程式需要多個工具列，您可以建立自己的根據預設工具列的精靈產生的程式碼的其他工具列的程式碼。  
  
 由於命令，如果您要顯示工具列，您需要:  
  
-   建立工具列編輯器中新增工具列資源並載入它在 `OnCreate` 用 [LoadToolbar](../Topic/CToolBar::LoadToolBar.md) 成員函式。  
  
-   將新的 [CToolBar](../mfc/reference/ctoolbar-class.md) 物件在您的主框架視窗類別。  
  
-   會在 `OnCreate` 的適當的函式呼叫固定或浮動工具列，設定其樣式，依此類推。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [MFC 工具列實作 \(如需工具列的概觀資訊\)](../mfc/mfc-toolbar-implementation.md)  
  
-   [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具列工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 類別  
  
-   [與工具列控制項](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
## 請參閱  
 [MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)