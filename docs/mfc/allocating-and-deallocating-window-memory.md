---
title: "配置和解除配置視窗記憶體 | Microsoft Docs"
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
  - "記憶體配置, 視窗物件"
  - "記憶體解除配置"
  - "記憶體解除配置, 視窗記憶體"
  - "視窗物件的儲存體"
  - "視窗物件的儲存體, 配置"
  - "視窗物件, 解除配置其記憶體"
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 配置和解除配置視窗記憶體
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不要使用 C\+\+ **delete** 運算子終結框架視窗或檢視。  取而代之，呼叫 `CWnd` 成員函式 `DestroyWindow`。  框架視窗，因此在與運算子 **new**的堆積應該配置。  當配置在堆疊上框架的全域時，框架視窗或小心。  在堆疊框架應該配置其他視窗盡可能。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [建立視窗](../mfc/creating-windows.md)  
  
-   [視窗解構序列](../mfc/window-destruction-sequence.md)  
  
-   [從 HWND 中斷連結 CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## 請參閱  
 [終結視窗物件](../mfc/destroying-window-objects.md)