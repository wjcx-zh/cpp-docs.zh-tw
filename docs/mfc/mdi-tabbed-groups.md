---
title: "MDI 索引標籤式群組 | Microsoft Docs"
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
  - "mdi, 索引標籤式群組"
  - "索引標籤式群組"
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# MDI 索引標籤式群組
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多重文件介面 \(MDI\) \(MDI\) 中索引群組功能啟用多重文件介面 \(MDI\) \(MDI\) 應用程式來顯示一或多個索引標籤的索引標籤式視窗 \(或群組，稱為 *索引標籤式群組*\) MDI 工作區。  具索引標籤的視窗可以垂直或水平置中對齊。  如果應用程式裝載多個 MDI 索引標籤式群組，群組由分隔器分隔。  
  
## 功能  
 下列是 MDI 索引標籤式群組功能：  
  
-   應用程式可以動態建立具索引標籤的視窗。  
  
-   應用程式可以水平或垂直對齊具索引標籤的視窗。  
  
-   具索引標籤的視窗群組由分隔器分隔。  使用分隔器，使用者可以調整成索引標籤式群組。  
  
-   使用者可以拖曳群組之間的個別選項。  
  
-   使用者可以拖曳個別選項建立新群組。  
  
-   您可以使用捷徑功能表，使用者可以捲動選項或建立新群組。  
  
-   應用程式可以儲存和載入具索引標籤的視窗配置。  
  
-   應用程式可以儲存和載入 MDI 文件清單。  
  
-   應用程式可以存取個別的索引標籤式群組和修改其參數。  
  
### 使用 MDI 索引標籤式群組  
 下列是工作經常執行與 MDI 索引標籤式群組：  
  
-   若要啟用 MDI 索引標籤式主框架視窗的群組，請呼叫 [CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md)。  這個方法的第二個參數是 `CMDITabInfo` 類別的執行個體。  在呼叫 `CMDIFrameWndEx::EnableMDITabbedGroups`之前，您可以使用預設參數或修改它們。  
  
-   若要修改屬性的屬性索引標籤式群組在執行階段，才能建立或修改 `CMDITabInfo` 物件並再次呼叫 `CMDIFrameWndEx::EnableMDITabbedGroups`  
  
-   若要取得 MDI 清單索引標籤式視窗，呼叫 `CMDIFrameWndEx::GetMDITabGroups`。  
  
-   若要建立新的 MDI 索引標籤式群組在現用旁邊的索引標籤式群組，由 `CMDIFrameWndEx::MDITabNewGroup`呼叫。  
  
-   若要將輸入焦點移至新的索引標籤式群組的上一個或下一個視窗，請呼叫 `CMDIFrameWndEx::MDITabMoveToNextGroup`。  
  
-   判斷視窗是否為 MDI 索引標籤式群組為 `CMDIFrameWndEx::IsMemberOfMDITabGroup`的成員。  
  
-   判斷 MDI 索引標籤或 MDI 索引標籤式群組是否為主框架視窗啟用，呼叫 `CMDIFrameWndEx::AreMDITabs`。  判斷 MDI 索引標籤式群組成員是否已啟用，呼叫 `CMDIFrameWndEx::IsMDITabbedGroup`。  
  
-   要顯示捷徑功能表，當使用者按一下選項或將它拖曳至另一個 MDI 索引標籤式群組時，請覆寫 `CMDIFrameWndEx`的 `CMDIFrameWndEx::OnShowMDITabContextMenu` 衍生類別。  如果您沒有執行這個方法，應用程式就會顯示捷徑功能表。  
  
-   要儲存設定 MDI 索引標籤式應用程式的群組，由 `CMDIFrameWndEx::SaveMDIState`呼叫。  若要載入先前儲存的 MDI 索引標籤式群組設定檔，呼叫 `CMDIFrameWndEx::LoadMDIState`。  您可以在 MDI 應用程式也可以呼叫這些方法載入或儲存開啟的文件清單。  如需儲存和載入 MDI 狀態的詳細資訊，請參閱 [CMDIFrameWndEx::LoadMDIState](../Topic/CMDIFrameWndEx::LoadMDIState.md)。  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [CMDIFrameWndEx 類別](../mfc/reference/cmdiframewndex-class.md)   
 [CMDIChildWndEx 類別](../mfc/reference/cmdichildwndex-class.md)   
 [CMDITabInfo Class](../mfc/reference/cmditabinfo-class.md)