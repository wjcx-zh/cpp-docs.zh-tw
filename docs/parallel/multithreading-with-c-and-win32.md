---
title: "使用 C 和 Win32 進行多執行緒處理 | Microsoft Docs"
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
  - "多執行緒 [C++], C 和 Win32"
  - "執行緒 [C]"
  - "執行緒 [C++], C 和 Win32"
  - "Visual C, 多執行緒"
  - "Win32 [C++], 多執行緒"
  - "Win32 應用程式 [C++], 多執行緒"
  - "Windows API [C++], 多執行緒"
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C 和 Win32 進行多執行緒處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Visual C\+\+ 提供以 Microsoft Windows \(Windows XP、Windows 2000、Windows NT、Windows Me 和 Windows 98\) 建立多執行緒應用程式的支援。  如果您的應用程式必須管理多個活動，例如同時接受鍵盤和滑鼠輸入，那麼您應該考慮使用一個以上的執行緒。  一個執行緒可以處理鍵盤輸入，而第二個執行緒篩選滑鼠動作。  第三個執行緒可以根據滑鼠和鍵盤執行緒的資料更新螢幕顯示。  同時，其他的執行緒可以存取磁碟檔案或從通訊連接埠取得資料。  
  
 利用 Visual C\+\+，有兩種方式可用來設計具有多執行緒的程式：使用 Microsoft Foundation Class \(MFC\) 程式庫或 C 執行階段程式庫和 Win32 API。  如需建立多執行緒應用程式的詳細資訊，請於詳讀下列有關 C 的多執行緒的主題後，請參閱[使用 C\+\+ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)。  
  
 這些主題會說明 Visual C\+\+ 中支援建立多執行緒程式的功能。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [多執行緒程式](../parallel/multithread-programs.md)  
  
-   [多執行緒的程式庫支援](../parallel/library-support-for-multithreading.md)  
  
-   [多執行緒的 Include 檔](../parallel/include-files-for-multithreading.md)  
  
-   [執行緒控制的 C 執行階段程式庫函式](../parallel/c-run-time-library-functions-for-thread-control.md)  
  
-   [多執行緒 C 程式範例](../parallel/sample-multithread-c-program.md)  
  
-   [撰寫多執行緒 Win32 程式](../parallel/writing-a-multithreaded-win32-program.md)  
  
-   [編譯和連結多執行緒程式](../parallel/compiling-and-linking-multithread-programs.md)  
  
-   [避免具有多執行緒程式的問題區域](../parallel/avoiding-problem-areas-with-multithread-programs.md)  
  
-   [執行緒區域儲存區 \(TLS\)](../parallel/thread-local-storage-tls.md)  
  
## 請參閱  
 [舊版程式碼的多執行緒支援 \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)