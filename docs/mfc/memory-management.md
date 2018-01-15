---
title: "記憶體管理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a9e31fc1136249f843aa5dc96a4caffcccc7a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management"></a>記憶體管理
本文件群說明如何使用 MFC 程式庫中與記憶體管理相關的通用服務。 記憶體配置可以分成兩個主要類型：框架配置和堆積配置。  
  
 兩個配置技術之間的主要差異是框架配置通常搭配實際的記憶體區塊，而使用時堆積配置則一定會給您指向記憶體區塊的指標。 兩種配置之間的另一個主要差異是框架物件會自動刪除，而堆積物件則必須由程式設計人員明確刪除。  
  
 如需適用於 Windows 程式中的記憶體管理的非 MFC 資訊，請參閱[記憶體管理](http://msdn.microsoft.com/library/windows/desktop/aa366779)Windows SDK 中。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [框架配置](../mfc/memory-management-frame-allocation.md)  
  
-   [堆積配置](../mfc/memory-management-heap-allocation.md)  
  
-   [陣列配置記憶體](../mfc/memory-management-examples.md)  
  
-   [從堆積解除配置陣列記憶體](../mfc/memory-management-examples.md)  
  
-   [配置記憶體的資料結構](../mfc/memory-management-examples.md)  
  
-   [物件配置記憶體](../mfc/memory-management-examples.md)  
  
-   [可調整大小的記憶體區塊](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)

