---
title: "記憶體管理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "記憶體"
  - "記憶體配置"
  - "記憶體配置, MFC"
  - "記憶體, 管理"
  - "MFC, 記憶體管理"
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記憶體管理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件的此群組描述如何使用 MFC 程式庫的通用服務與記憶體管理相關。  記憶體配置可以分成兩個主要類型:設定框架和堆疊配置。  
  
 兩個組態技術之間的主要差異是與您通常與實際記憶體區塊一起使用的框架，配置，而使用堆積配置您一定會將指標的記憶體區塊。  兩種配置之間的另一個主要差異是框架物件自動刪除，反之，必須由程式設計人員明確刪除堆積物件。  
  
 如需記憶體管理的非 MFC 資訊在視窗的程式，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [記憶體管理](http://msdn.microsoft.com/library/windows/desktop/aa366779) 。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [框架配置](../mfc/memory-management-frame-allocation.md)  
  
-   [堆積配置](../mfc/memory-management-heap-allocation.md)  
  
-   [配置陣列的記憶體。](../mfc/memory-management-examples.md)  
  
-   [解除配置陣列的記憶體從堆積](../mfc/memory-management-examples.md)  
  
-   [配置資料結構的記憶體](../mfc/memory-management-examples.md)  
  
-   [配置物件的記憶體。](../mfc/memory-management-examples.md)  
  
-   [可調整大小的記憶體區塊](../mfc/memory-management-resizable-memory-blocks.md)  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)