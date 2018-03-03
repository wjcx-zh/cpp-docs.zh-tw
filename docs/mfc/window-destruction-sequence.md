---
title: "視窗解構序列 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b873d51f585336425537756064582eb709988f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="window-destruction-sequence"></a>視窗解構序列
在 MFC 架構中，當使用者關閉框架視窗時，視窗的預設[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 當 Windows 視窗終結時呼叫之最後一個成員函式[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，其會進行一些清除，呼叫[預設](../mfc/reference/cwnd-class.md#default)成員函式以執行 Windows 清除，最後再呼叫虛擬成員函式[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)實作`PostNcDestroy`刪除 c + + 視窗物件。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [中斷連結從 HWND CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>請參閱  
 [終結視窗物件](../mfc/destroying-window-objects.md)

