---
title: "配置和解除配置視窗記憶體 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4933ea9f079a18c4147db2da96b99653c5ddda26
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="allocating-and-deallocating-window-memory"></a>配置和解除配置視窗記憶體
不使用 c + +**刪除**終結框架視窗或檢視表的運算子。 請改為呼叫`CWnd`成員函式`DestroyWindow`。 框架視窗，因此，應該會在堆積上配置運算子**新**。 配置框架視窗上的堆疊框架或全域時務必謹慎。 其他視窗應該盡可能在堆疊框架上配置。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [建立視窗](../mfc/creating-windows.md)  
  
-   [視窗解構序列](../mfc/window-destruction-sequence.md)  
  
-   [中斷連結從 HWND CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>另請參閱  
 [終結視窗物件](../mfc/destroying-window-objects.md)

