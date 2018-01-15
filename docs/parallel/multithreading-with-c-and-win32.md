---
title: "使用 C 和 Win32 進行多執行緒處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 30c7833a4df80669b6223f1fe6b1ccceed0257cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-win32"></a>使用 C 和 Win32 進行多執行緒處理
Microsoft Visual c + + 提供支援使用 Microsoft Windows 中建立多執行緒應用程式： Windows XP、 Windows 2000、 Windows NT、 Windows Me，和 Windows 98。 您應該考慮使用多個執行緒，如果您的應用程式需要管理多個活動，例如同時鍵盤和滑鼠輸入。 一個執行緒可以處理鍵盤輸入，而第二個執行緒篩選滑鼠動作。 第三個執行緒可以更新的滑鼠和鍵盤執行緒資料的顯示畫面。 同時，其他執行緒可以存取磁碟檔案，或從通訊連接埠取得資料。  
  
 使用 Visual c + + 中，有兩種多執行緒程式： 使用 Microsoft Foundation Class (MFC) 程式庫或 C 執行階段程式庫和 Win32 API。 使用 MFC 建立多執行緒應用程式的詳細資訊，請參閱[多執行緒 c + + 和 MFC](../parallel/multithreading-with-cpp-and-mfc.md)閱讀下列有關多執行緒 c 中的主題之後  
  
 這些主題說明 Visual c + + 中可支援多執行緒程式建立的功能。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [什麼多執行緒即將](../parallel/multithread-programs.md)  
  
-   [程式庫支援多執行緒處理](../parallel/library-support-for-multithreading.md)  
  
-   [包含檔案的多執行緒處理](../parallel/include-files-for-multithreading.md)  
  
-   [執行緒控制的 C 執行階段程式庫函式](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [範例 C 中的多執行緒程式](../parallel/sample-multithread-c-program.md)  
  
-   [撰寫多執行緒 Win32 程式](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [編譯和連結多執行緒程式](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [避免具有多執行緒程式的問題區域](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [執行緒區域儲存區 (TLS)](../parallel/thread-local-storage-tls.md)  
  
## <a name="see-also"></a>請參閱  
 [舊版程式碼的多執行緒支援 (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)