---
title: "初始化 CWnd 物件的時機 | Microsoft Docs"
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
  - "CWnd 物件, 已附加 HWND 時"
  - "CWnd 物件, 初始化時機"
  - "HWND, 已附加到 CWnd 物件時"
  - "初始化 CWnd 物件"
  - "初始化物件, CWnd"
  - "視窗物件, 初始化 CWnd 的時機"
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 初始化 CWnd 物件的時機
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您不能建立自己的子視窗或呼叫 `CWnd`的建構函式衍生物件的任何 Windows API 函式。  這是因為， `CWnd` 物件的 `HWND` 尚未建立。  大部分視窗專屬初始化，例如將子視窗，請在 [OnCreate](../Topic/CWnd::OnCreate.md) 訊息處理常式必須完成。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
-   [文件\/檢視建立](../mfc/document-view-creation.md)  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)