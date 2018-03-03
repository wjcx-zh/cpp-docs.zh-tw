---
title: "更新狀態列窗格的文字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0fb0f9bdaa032340256eee4781bfd775767f62ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>更新狀態列窗格的文字
本文說明如何變更 MFC 狀態列窗格中顯示的文字。 狀態列，類別的視窗物件[CStatusBar](../mfc/reference/cstatusbar-class.md) — 包含多個 「 窗格 」。 每個窗格是您可用來顯示資訊的 [狀態] 列的一個矩形區域。 比方說，許多應用程式會顯示在最右邊的窗格中按下 CAPS LOCK、 NUM LOCK 和其他按鍵的狀態。 應用程式通常也會顯示資訊文字中最左邊的窗格 （窗格 0），有時也稱為 「 訊息窗格 」。 例如，預設 MFC 狀態列會使用 [訊息] 窗格來顯示字串，用以說明目前所選取的功能表項目或工具列按鈕。 在圖[狀態列](../mfc/status-bar-implementation-in-mfc.md)顯示從應用程式精靈建立 MFC 應用程式的狀態列。  
  
 根據預設，MFC 不會啟用`CStatusBar`窗格時它會建立 [] 窗格。 若要啟用的窗格中，您必須使用`ON_UPDATE_COMMAND_UI`巨集的每個狀態窗格橫條圖和更新 窗格。 因為窗格不會傳送**WM_COMMAND**訊息 （不是像工具列按鈕），您必須手動輸入程式碼。  
  
 例如，假設有一個窗格`ID_INDICATOR_PAGE`做為其命令識別碼，它會包含文件中的目前頁碼。 下列程序描述如何在狀態列中建立新的窗格。  
  
### <a name="to-make-a-new-pane"></a>若要建立新窗格  
  
1.  定義窗格的命令 id。  
  
     在**檢視**功能表上，按一下 **資源檢視**。 以滑鼠右鍵按一下專案資源，然後按一下**資源符號**。 在 [資源符號] 對話方塊中，按一下`New`。 輸入的命令識別碼名稱： 例如， `ID_INDICATOR_PAGE`。 指定識別碼的值，或接受 [資源符號] 對話方塊所建議的值。 例如，對於`ID_INDICATOR_PAGE`，接受預設值。 關閉 [資源符號] 對話方塊。  
  
2.  定義要在窗格中顯示的預設字串。  
  
     使用資源檢視中開啟，按兩下**字串資料表**列出您的應用程式的資源類型的視窗。 與**字串資料表**編輯器中開啟，請選擇**新字串**從**插入**功能表。 在字串屬性 視窗中，選取窗格的命令 ID (例如， `ID_INDICATOR_PAGE`) 輸入的預設字串值，例如 「 頁面 」。 關閉字串編輯器。 （您需要的預設字串，以避免編譯器錯誤）。  
  
3.  加入至窗格**指標**陣列。  
  
     在檔案 MAINFRM。CPP，找出**指標**陣列。 這個陣列會列出所有 [狀態] 列中的指標，從左到右的順序的命令 Id。 陣列中的適當點，請輸入窗格的命令識別碼，如下所示的`ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 在窗格中顯示文字的建議的方式是呼叫**SetText**類別成員函式`CCmdUI`中窗格的更新處理常式函式。 例如，您可能想要設定整數變數`m_nPage`包含目前的頁碼和使用**SetText**窗格的文字設該數字的字串版本。  
  
> [!NOTE]
>  **SetText**建議使用方法。 可執行此工作在較低層級呼叫`CStatusBar`成員函式`SetPaneText`。 即便如此，您仍然需要更新處理常式。 沒有這類處理常式的窗格，MFC 會自動停用 窗格中，清除其內容。  
  
 下列程序示範如何使用更新的處理常式函式在窗格中顯示的文字。  
  
#### <a name="to-make-a-pane-display-text"></a>若要讓文字顯示 窗格  
  
1.  加入命令的命令更新處理常式。  
  
     手動加入處理常式中的原型，如下所示的`ID_INDICATOR_PAGE`（在 MAINFRM。H):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  在適當的。CPP 檔案中，加入處理常式的定義，如下所示的`ID_INDICATOR_PAGE`（在 MAINFRM。CPP):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     此處理常式的最後三行所顯示文字的程式碼。  
  
3.  在適當的訊息對應中，加入`ON_UPDATE_COMMAND_UI`巨集，如下所示的`ID_INDICATOR_PAGE`（在 MAINFRM。CPP):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 一旦您定義的值`m_nPage`成員變數 (類別的`CMainFrame`)，這項技術讓應用程式會更新其他指標的相同方式出現在窗格中閒置處理期間的頁碼。 如果`m_nPage`變更下, 一步的閒置迴圈期間顯示中有所變更。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [更新使用者介面物件 （如何更新程式狀況變更工具列按鈕和功能表項目）](../mfc/how-to-update-user-interface-objects.md)  
  
## <a name="see-also"></a>請參閱  
 [在 MFC 中的狀態列實作](../mfc/status-bar-implementation-in-mfc.md)   
 [CStatusBar 類別](../mfc/reference/cstatusbar-class.md)
