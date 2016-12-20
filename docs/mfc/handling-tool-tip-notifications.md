---
title: "處理工具提示告知 | Microsoft Docs"
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
  - "CToolBarCtrl 類別, 處理告知"
  - "告知, 工具提示"
  - "工具提示 [C++], 告知"
  - "TOOLTIPTEXT 結構"
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理工具提示告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您指定 `TBSTYLE_TOOLTIPS` 樣式時，工具列建立和管理工具提示控制項。  工具提示是包含描述工具列按鈕的文字行的小型快顯視窗。  只有當使用者在工具列按鈕和分葉上將游標放置它仍為大約二分之一秒時，工具提示會隱藏，則會發生。  工具提示在游標周圍顯示。  
  
 在工具提示中顯示之前， **TTN\_NEEDTEXT** 會傳送通知訊息至工具列的主控視窗擷取按鈕的描述文字。  如果工具列的主控視窗是 `CFrameWnd` 視窗，工具提示會顯示，而不需要任何額外工作，，因為 `CFrameWnd` 的 **TTN\_NEEDTEXT** 通知的預設處理常式。  如果工具列的主控視窗不是衍生自 `CFrameWnd`，例如對話方塊或表單檢視，您必須將項目加入至您的主控視窗的訊息對應和提供訊息對應的通知處理常式。  對您的主控視窗的訊息對應的項目如下:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/CPP/handling-tool-tip-notifications_1.cpp)]  
  
## 備註  
 `memberFxn`  
 要呼叫的，當文字此按鈕所需的成員函式。  
  
 請注意工具提示的 ID 一定是 0。  
  
 除了通知 **TTN\_NEEDTEXT** 之外，工具提示控制項可以傳送通知給下列工具列控制項:  
  
|告知|意義|  
|--------|--------|  
|**TTN\_NEEDTEXTA**|工具提示控制項需要 ASCII 文字 \(僅適用於 Windows 95\)|  
|**TTN\_NEEDTEXTW**|工具提示控制項要求 UNICODE 文字 \(僅適用於 Windows NT\)|  
|**TBN\_HOTITEMCHANGE**|作用中指示 \(反白顯示\) 的項目已變更。|  
|**NM\_RCLICK**|表示使用者按一下滑鼠右鍵按一下按鈕。|  
|**TBN\_DRAGOUT**|表示使用者按一下按鈕並拖曳指標按鈕。  它可讓應用程式實作從工具列按鈕的拖放。  在接收這個告知時，應用程式會開始拖放作業。|  
|**TBN\_DROPDOWN**|表示使用者按一下使用 **TBSTYLE\_DROPDOWN** 樣式的按鈕。|  
|**TBN\_GETOBJECT**|表示使用者已捲動到使用 **TBSTYLE\_DROPPABLE** 樣式按鈕的指標。|  
  
 如需的範例處理常式函式和更多有關啟用工具提示，請參閱 [工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。  
  
## 請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)