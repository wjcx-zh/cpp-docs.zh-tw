---
title: "從 HWND 中斷連結 CWnd | Microsoft Docs"
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
  - "CWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd 物件, 從 HWND 中斷連結"
  - "Detach 方法 (CWnd 類別)"
  - "從 HWND 中斷連結 CWnd"
  - "HWND, 從中中斷連結 CWnd"
  - "從 CWnd 移除 HWND"
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從 HWND 中斷連結 CWnd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您需要規避物件`HWND` 關聯性， MFC 提供另一個 `CWnd` 成員函式，從 Windows 視窗斷開 C\+\+ 視窗物件的[Detach](../Topic/CWnd::Detach.md)函式。  這可以避免解構函式在物件被終止時終結Windows的視窗物件。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [建立視窗](../mfc/creating-windows.md)  
  
-   [視窗解構序列](../mfc/window-destruction-sequence.md)  
  
-   [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)