---
title: "終結視窗物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67d2df7d72de079a0408847c433000a652ac6aaa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="destroying-window-objects"></a>終結視窗物件
必須小心使用您自己的子視窗終結時使用者完成與視窗的 c + + 視窗物件。 不會終結這些物件，如果您的應用程式將不會復原其記憶體。 幸運的是，架構會管理視窗的解構與框架視窗、 檢視和對話方塊的建立。 如果您建立其他視窗，您必須負責終結它們。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [視窗解構序列](../mfc/window-destruction-sequence.md)  
  
-   [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [中斷連結從 HWND CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [一般視窗建立順序](../mfc/general-window-creation-sequence.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>另請參閱  
 [視窗物件](../mfc/window-objects.md)

