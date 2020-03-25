---
title: 舊版程式碼的多執行緒支援 (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 6f76ff42d2e28afe251ce234220051111736d3c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215081"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>舊版程式碼的多執行緒支援 (Visual C++)

視覺C++效果可讓您同時執行多個平行線程。 有了多執行緒，您可以微調背景工作、管理輸入的同步串流、管理使用者介面等等。

## <a name="in-this-section"></a>本節內容

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)<br/>
提供使用 Microsoft Windows 建立多執行緒應用程式的支援

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)<br/>
描述哪些進程和執行緒，以及 MFC 對多執行緒處理的方法。

[多執行緒和地區設定](multithreading-and-locales.md)<br/>
討論在多執行緒應用程式中使用 C 執行時間程式庫和C++標準程式庫的地區設定功能時，所發生的問題。

## <a name="related-sections"></a>相關章節

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
代表應用程式內執行的執行緒。

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
描述純虛擬類別，提供 Win32 中同步處理物件的通用功能。

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
代表信號，這是一個同步處理物件，可讓一或多個進程中的執行緒數目有限，以存取資源。

[CMutex](../mfc/reference/cmutex-class.md)<br/>
代表 Mutex，即允許執行緒互斥 (Mutually Exclusive) 存取資源的同步物件。

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
代表重要區段，這是一個同步處理物件，一次允許一個執行緒存取資源或區段的程式碼。

[CEvent](../mfc/reference/cevent-class.md)<br/>
表示事件，這是一個同步處理物件，可讓一個執行緒通知另一個事件已發生。

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
代表多執行緒程式用來控制多個資源存取的存取控制機制。

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
代表多執行緒程式用來控制單一資源存取的存取控制機制。
