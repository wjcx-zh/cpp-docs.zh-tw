---
title: "更新狀態列窗格的文字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBar 類別, 更新"
  - "ON_UPDATE_COMMAND_UI 巨集"
  - "窗格, 狀態列"
  - "SetText 方法"
  - "狀態列, 更新"
  - "文字, 狀態列"
  - "更新使用者介面物件"
  - "使用者介面物件, 更新"
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 更新狀態列窗格的文字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何變更出現在 MFC 狀態列窗格的文字。  狀態列—類別 [CStatusBar](../mfc/reference/cstatusbar-class.md) 視窗物件—包含數個「Pane」。每一個窗格可用來顯示資訊狀態列的矩形區域。  例如，許多應用程式顯示 CAPS LOCK、NUM LOCK 和其他型別的狀況最右邊的窗格。  應用程式通常也會顯示在窗格 \(0\) 的資訊文字，有時稱為訊息窗格最左邊窗格」。例如，預設 MFC 狀態列使用訊息窗格顯示說明目前選取的功能表項目或工具列按鈕的字串。  在 [狀態列](../mfc/status-bar-implementation-in-mfc.md) 的圖表會顯示從應用程式精靈建立的 MFC 應用程式中的狀態列。  
  
 根據預設，在建立窗格時， MFC 並未啟用 `CStatusBar` 窗格中。  若要啟動窗格，您必須在狀態列的每一個窗格使用 `ON_UPDATE_COMMAND_UI` 巨集和更新窗格。  由於窗格不傳送 **WM\_COMMAND** 資訊 \(而不是像工具列按鈕\)，您必須手動輸入程式碼。  
  
 例如，假設有一個窗格 `ID_INDICATOR_PAGE` 做為它的命令識別項，並且在文件中目前的頁碼。  下列程序描述如何在狀態列的新的窗格。  
  
### 將新的窗格  
  
1.  定義窗格的命令 ID.  
  
     在 \[**檢視**\] 功能表上按一下 \[**資源檢視**\]。  以滑鼠右鍵按一下專案資源，然後按一下 \[**資源符號**\]。  在資源符號對話方塊中，選擇 `New`。  輸入命令 ID 名稱:例如， `ID_INDICATOR_PAGE`。  為指定 ID 值或接受資源符號對話方塊的建議值。  例如，對於 `ID_INDICATOR_PAGE`，請接受預設值。  關閉資源符號對話方塊。  
  
2.  定義預設字串顯示在窗格。  
  
     資源檢視中開啟，按兩下列出應用程式的資源類型視窗的 **String Table** 。  開啟 **String Table** 的編輯器，從 **Insert** 功能表選擇 **New String** 。  在字串屬性視窗中，選取您的窗格的命令 ID \(例如 `ID_INDICATOR_PAGE`\)，並輸入一個預設字串值，例如「Page」。  關閉字串編輯器。\(您需要預設字串避免編譯器錯誤\)。  
  
3.  將窗格加入 **indicators** 陣列。  
  
     在檔案 MAINFRM.CPP，找出 **indicators** 陣列。  這個陣列清單由左至右排列任何的 ID 狀態列的指示器，順序。  在陣列中的適當\]，請輸入您的窗格的命令 ID，如下所示為 `ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 這個建議的方式顯示在窗格的文字會呼叫類別的 `CCmdUI` **SetText** 成員函式以更新處理函式的窗格中。  例如，您可以將包含這個目前的頁碼和使用 **SetText** 設定窗格文字到該數字字串版本的整數變數的 `m_nPage` 。  
  
> [!NOTE]
>  建議 **SetText** 方法。  執行這項工作在稍微較低層級都可以透過呼叫 `CStatusBar` 成員函式 `SetPaneText`。  即使如此，您還是必須更新處理常式。  沒有窗格的這種處理常式， MFC 會自動停用窗格，清除其內容。  
  
 下列程序示範如何使用 Update 處理函式顯示在窗格中的文字。  
  
#### 執行窗格中顯示文字  
  
1.  加入命令的命令的處理常式。  
  
     請手動加入處理常式的原型，如下所示為 `ID_INDICATOR_PAGE` \(在 MAINFRM.H\):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  在適當的 .CPP 檔案中，加入處理常式的定義，如下所示為 `ID_INDICATOR_PAGE` \(在 MAINFRM.CPP\):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     這個處理常式最後三行是顯示文字的程式碼。  
  
3.  在適當的訊息對應，請將 `ON_UPDATE_COMMAND_UI` 巨集，如下所示為 `ID_INDICATOR_PAGE` \(在 MAINFRM.CPP\):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 一旦定義了 `m_nPage` 成員變數的值 \( `CMainFrame`類別\)，這項技術原因出現的頁碼窗格類似於在處理的延遲期間應用程式更新其他指示器。  如果 `m_nPage` 變更時，在下閒置迴圈時，會顯示變更。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [更新使用者介面物件 \(如何更新工具列按鈕和功能表項目為程式條件變更\)](../mfc/how-to-update-user-interface-objects.md)  
  
## 請參閱  
 [MFC 中的狀態列實作](../mfc/status-bar-implementation-in-mfc.md)   
 [CStatusBar Class](../mfc/reference/cstatusbar-class.md)