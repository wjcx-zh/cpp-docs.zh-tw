---
title: "處理反映訊息 | Microsoft Docs"
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
  - "訊息處理, 反映訊息"
  - "反映訊息, 處理"
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 處理反映訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

訊息反映可讓您處理控制項的訊息，例如 `WM_CTLCOLOR`、 **WM\_COMMAND**和 **WM\_NOTIFY**，在控制項中。  這可讓控制項獨立和可移植。  機制與 Windows 通用控制項以及與 ActiveX 控制項 \(先前稱為 OLE automation 控制項\)。  
  
 訊息反映可讓您立即重複使用 `CWnd`衍生類別。  使用特殊 **ON\_XXX\_REFLECT** 訊息對應項，訊息會透過 [CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)運作，例如， **ON\_CTLCOLOR\_REFLECT** 和 **ON\_CONTROL\_REFLECT**。  [Technical Note 62](../mfc/tn062-message-reflection-for-windows-controls.md) 會更詳細說明訊息反映。  
  
## 您想要執行甚麼工作？  
  
-   [進一步了解訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [實作通用控制項的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [實作 ActiveX 控制項的訊息反映](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## 請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)