---
title: 多執行緒支援較舊的程式碼 （Visual c + +） |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b1b301186036460acc07a526267503da8b97678
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132098"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>舊版程式碼的多執行緒支援 (Visual C++)
Visual c + + 可讓您有同時執行的多個並行執行緒。 使用多執行緒處理，您可以分割背景工作、 管理同時的輸入資料流、 管理使用者介面，以及其他等等。  
  
## <a name="in-this-section"></a>本節內容  
 
[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)  
提供支援使用 Microsoft Windows 建立多執行緒應用程式  
  
[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)  
描述什麼是處理序和執行緒，以及 MFC 的方法進行多執行緒處理時。  
  
[多執行緒和地區設定](multithreading-and-locales.md)  
討論使用 C 執行階段程式庫和 c + + 標準程式庫中的多執行緒應用程式的地區設定功能時所發生的問題。  
  
## <a name="related-sections"></a>相關章節  
 
[CWinThread](../mfc/reference/cwinthread-class.md)  
代表應用程式內執行的執行緒。  
  
[CSyncObject](../mfc/reference/csyncobject-class.md)  
說明純虛擬類別，可提供在 Win32 中同步處理物件通用的功能。  
  
[CSemaphore](../mfc/reference/csemaphore-class.md)  
代表號誌，這是允許限定的數量的執行緒在一或多個處理序中存取資源的同步處理物件。  
  
[CMutex](../mfc/reference/cmutex-class.md)  
代表 Mutex，即允許執行緒互斥 (Mutually Exclusive) 存取資源的同步物件。  
  
[CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
代表關鍵區段中，也就是允許一個執行緒存取資源或程式碼區段，一次同步處理物件。  
  
[CEvent](../mfc/reference/cevent-class.md)  
代表事件，這是允許一個執行緒通知另一個在事件發生的同步處理物件。  
  
[CMultiLock](../mfc/reference/cmultilock-class.md)  
代表多執行緒程式用來控制多個資源存取的存取控制機制。  
  
[CSingleLock](../mfc/reference/csinglelock-class.md)  
代表多執行緒程式用來控制單一資源存取的存取控制機制。  