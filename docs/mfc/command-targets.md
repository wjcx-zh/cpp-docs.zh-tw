---
title: "命令目標 | Microsoft Docs"
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
  - "命令對應"
  - "命令傳送, 命令目標"
  - "命令目標"
  - "訊息, 命令"
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 命令目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個圖形 [在 Framework 的命令](../mfc/user-interface-objects-and-command-ids.md) 顯示使用者介面物件之間的連接，例如按一下物件時功能表項目和執行產生的命令的框架呼叫的處理常式函式。  
  
 Windows 直接傳送不是命令訊息的訊息至視窗，而其訊息處理常式則接著被呼叫。  不過，這個框架傳送命令給很多個候選物件 — 稱為命令目標 — 通常是叫用命令的處理常式。  處理常式函式運作命令和標準 Windows 訊息的相同方式，但是，呼叫的機制不同，如 [Framework 如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)所說明。  
  
## 請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)