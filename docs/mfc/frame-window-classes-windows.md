---
title: "框架視窗類別 (Windows) | Microsoft Docs"
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
  - "vc.classes.frame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架視窗類別, 參考"
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架視窗類別 (Windows)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架視窗是架構應用程式或應用程式中的視窗。  框架視窗通常包含其他視窗，例如檢視、工具列和狀態列。  在 `CMDIFrameWnd`的情況下，它們可能間接包含 `CMDIChildWnd` 物件。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 應用程式的主框架視窗的基底類別。  也是任何其他的基底類別框架視窗類別。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 應用程式的主框架視窗的基底類別。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 應用程式的文件框架視窗的基底類別。  
  
 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)  
 通常在浮動工具列周圍出現的半高度框架視窗。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 當伺服器文件就地編輯時，提供檢視框架視窗。  
  
## 相關類別  
 `CMenu` 類別提供存取應用程式的功能表的介面。  在執行階段動態操作功能表示有用的；例如在根據內容加入或刪除功能表項目時。  雖然功能表最常用於框架視窗，但也可以使用對話方塊和其他 nonchild 視窗。  
  
 [CMenu](../mfc/reference/cmenu-class.md)  
 封裝 `HMENU` 控制代碼應用程式的功能表列和快顯功能表。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)