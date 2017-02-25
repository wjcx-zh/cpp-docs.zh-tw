---
title: "框架視窗類別 (架構) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.frame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架視窗類別, 文件/檢視架構"
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 框架視窗類別 (架構)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在文件\/檢視架構中，框架視窗是包含檢視視窗的視窗。  它們也支援附加的控制列。  
  
 在多重文件介面 \(MDI\) 應用程式，主視窗衍生自 `CMDIFrameWnd`。  它會間接包含文件的框架，即 `CMDIChildWnd` 物件。  反之，`CMDIChildWnd` 物件，包含文件的檢視。  
  
 在單一文件介面 \(SDI\) 應用程式，主視窗，衍生自 `CFrameWnd`，包含目前文件的檢視。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 應用程式的主框架視窗的基底類別。  也是任何其他的基底類別框架視窗類別。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 應用程式的主框架視窗的基底類別。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 應用程式的文件框架視窗的基底類別。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 當伺服器文件就地編輯時，提供檢視框架視窗。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)