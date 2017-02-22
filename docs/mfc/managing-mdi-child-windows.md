---
title: "管理 MDI 子視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MDICLIENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "子視窗"
  - "子視窗, 和 MDICLIENT 視窗"
  - "框架視窗 [C++], MDI 子視窗"
  - "MDI [C++], 子視窗"
  - "MDI [C++], 框架視窗"
  - "MDICLIENT 視窗"
  - "視窗 [C++], MDI"
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 管理 MDI 子視窗
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MDI 主框架視窗 \(每一應用程式\) 包含呼叫 **MDICLIENT** 視窗的特殊子視窗。  **MDICLIENT** 視窗處理主框架視窗的工作區，然後，本身具有子視窗:文件視窗，衍生自 `CMDIChildWnd`。  由於文件視窗是框架視窗 \(MDI 子視窗\)，也可以有自己的子系。  在所有這些情況，父視窗管理其子視窗並將一些命令給它們。  
  
 在 MDI 框架視窗，框架視窗處理 **MDICLIENT** 視窗，重新調整與控制列結合。  **MDICLIENT** 視窗，然後，處理所有 MDI 子框架視窗。  下圖顯示 MDI 框架視窗、其 **MDICLIENT** 視窗及其子文件框架視窗之間的關聯性。  
  
 ![MDI 框架視窗中的子視窗](../mfc/media/vc37gb1.png "vc37GB1")  
MDI 框架視窗和子視窗  
  
 如果有的話， MDI 框架視窗與目前 MDI 子視窗也一起運作。  在嘗試處理它們本身前， MDI 框架視窗委派命令訊息至 MDI 子系。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
-   [框架視窗樣式](../mfc/frame-window-styles-cpp.md)  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)