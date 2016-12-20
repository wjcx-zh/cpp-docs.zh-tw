---
title: "記憶體管理：可調整大小的記憶體區塊 | Microsoft Docs"
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
  - "區塊, 記憶體配置"
  - "記憶體配置, 記憶體區塊大小"
  - "記憶體區塊, 配置"
  - "記憶體區塊, 可調整大小"
  - "記憶體, 損毀"
  - "可調整大小的記憶體區塊"
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 記憶體管理：可調整大小的記憶體區塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**new** 和 **delete** 運算子，描述在這篇文章 [記憶體管理:範例](../mfc/memory-management-examples.md)，獲益配置和解除配置固定大小的記憶體區塊和物件。  有時候，您的應用程式可能需要可調整大小的記憶體區塊。  您必須使用標準 C 執行階段程式庫函式 [malloc](../c-runtime-library/reference/malloc.md)、 [realloc](../c-runtime-library/reference/realloc.md)和 [可用](../c-runtime-library/reference/free.md) 來管理堆積的可調整大小的記憶體區塊。  
  
> [!IMPORTANT]
>  混合 **new** 和 **delete** 運算子在相同記憶體區塊的可調整大小的記憶體配置函式會在 MFC 偵錯版本的損毀記憶體。  您不應該使用在記憶體區塊的 `realloc` 配置與 **new**。  同樣地，您不應該配置有 **new** 運算子的記憶體區塊和刪除它與 **free**，或使用記憶體區塊的 **delete** 運算子配置的 `malloc`。  
  
## 請參閱  
 [記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)