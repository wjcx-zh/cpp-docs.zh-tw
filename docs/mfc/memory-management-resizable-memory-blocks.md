---
title: "記憶體管理： 可調整大小的記憶體區塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fce06d27a091ad1740c882367358cf69a6dc3e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-resizable-memory-blocks"></a>記憶體管理：可調整大小的記憶體區塊
**新**和**刪除**運算子，文件所述[記憶體管理： 範例](../mfc/memory-management-examples.md)，適合用於配置和解除配置的固定大小的記憶體區塊和物件。 有時候，您的應用程式可能需要可調整大小的記憶體區塊。 您必須使用標準 C 執行階段程式庫函式[malloc](../c-runtime-library/reference/malloc.md)， [realloc](../c-runtime-library/reference/realloc.md)，和[可用](../c-runtime-library/reference/free.md)來管理堆積上的可調整大小的記憶體區塊。  
  
> [!IMPORTANT]
>  混合**新**和**刪除**具有相同的記憶體區塊的可調整大小的記憶體配置函式的運算子會導致損毀的記憶體，在 MFC 的偵錯版本。 您不應該使用`realloc`上的記憶體區塊，以配置**新**。 同樣地，您不應該配置的記憶體區塊**新**運算子並將它與刪除**可用**，或使用**刪除**運算子，在以所配置的記憶體區塊`malloc`.  
  
## <a name="see-also"></a>請參閱  
 [記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)

