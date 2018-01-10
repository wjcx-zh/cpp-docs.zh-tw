---
title: "多執行緒支援對舊版程式碼 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1037b8b81c9286ac1b1dd9303294b4300e7c9309
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-support-for-older-code-visual-c"></a>舊版程式碼的多執行緒支援 (Visual C++)
Visual c + + 可讓您能夠同時執行多個執行緒同時執行。 使用多執行緒處理，您可以分割背景工作、 管理同時的輸入資料流、 管理使用者介面，以及執行更多。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)  
 提供支援使用 Microsoft Windows 中建立多執行緒應用程式  
  
 [使用 C++ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)  
 描述什麼是處理序和執行緒，以及 MFC 的方法多執行緒時。  
  
 [多執行緒和地區設定](../parallel/multithreading-and-locales.md)  
 討論使用 C 執行階段程式庫和 c + + 標準程式庫中的多執行緒應用程式的地區設定功能時，會發生的問題。  
  
## <a name="related-sections"></a>相關章節  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 代表應用程式內執行的執行緒。  
  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 描述提供在 Win32 中的同步處理物件常見功能的純虛擬類別。  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 代表信號，即允許有限的數目的執行緒在一或多個處理序中存取資源的同步處理物件。  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 代表 Mutex，即允許執行緒互斥 (Mutually Exclusive) 存取資源的同步物件。  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 代表關鍵區段中，這是在存取資源或程式碼區段的時間讓一個執行緒的同步處理物件。  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 表示事件，這是可讓一個執行緒通知發生事件的另一個執行緒的同步處理物件。  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 代表多執行緒程式用來控制多個資源存取的存取控制機制。  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 代表多執行緒程式用來控制單一資源存取的存取控制機制。  
  
 [(NOTINBUILD)Visual c + + 程式設計方法](http://msdn.microsoft.com/en-us/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 提供主題連結，這些主題將描述 Visual C++ 程式庫的概念性資訊，以及討論各種程式碼撰寫技術和技巧。