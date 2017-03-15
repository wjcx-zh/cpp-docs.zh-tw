---
title: "非命令訊息如何連接其處理常式 | Microsoft Docs"
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
  - "訊息處理 [C++], 非命令訊息"
  - "訊息 [C++], 傳送"
  - "非命令訊息"
  - "Windows 訊息 [C++], 傳送"
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 非命令訊息如何連接其處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不同於命令，標準 Windows 訊息通過指示系統物件被路由，而是由視窗傳送訊息的視窗通常處理。  視窗可能是框架視窗 \(Main Frame Window\)、MDI 子視窗、標準控制項、對話方塊、檢視，或子視窗。  
  
 在執行階段，每個視窗視窗附加至有關聯的訊息對應和處理函式的視窗物件 \(直接或間接衍生自 `CWnd`\)。  架構會使用訊息對應—至於為命令時傳入訊息與針對處理常式。  
  
## 請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)