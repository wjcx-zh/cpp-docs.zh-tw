---
title: "啟用工具提示 | Microsoft Docs"
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
  - "啟用工具提示"
  - "初始化工具提示"
  - "工具提示 [C++], 啟用"
  - "工具提示 [C++], 初始化"
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 啟用工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以啟用支援工具提示視窗的子控制項 \(例如在表單檢視或對話方塊的控制項\)。  
  
### 啟用視窗的子控制項的工具提示  
  
1.  呼叫您想提供工具提示視窗的 `EnableToolTips` 。  
  
2.  針對您的 [TTN\_NEEDTEXT 通知](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) 處理常式的每個控制項的字串。  處理常式是在包含子控制項視窗的訊息對應 \(例如，您的表單檢視類別\)。  這個處理常式會識別控制項並將 **pszText** 指定工具提示控制項使用的文字的函式。  
  
## 請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)