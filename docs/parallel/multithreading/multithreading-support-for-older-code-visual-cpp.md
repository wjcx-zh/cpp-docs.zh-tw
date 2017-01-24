---
title: "舊版程式碼的多執行緒支援 (Visual C++) | Microsoft Docs"
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
  - "並行程式設計 [C++]"
  - "多個並行執行緒"
  - "多個執行緒"
  - "多執行緒 [C++]"
  - "多執行緒 [C++], 關於多執行緒"
  - "程式設計 [C++], 多執行緒"
  - "執行緒 [C++]"
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 舊版程式碼的多執行緒支援 (Visual C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 允許您有多個同時執行的並行執行緒。  有了多執行緒處理，您可以分割背景工作、管理同時的輸入資料流、管理使用介面等等。  
  
## 本章節內容  
 [使用 C 和 Win32 進行多執行緒處理](../../parallel/multithreading-with-c-and-win32.md)  
 提供使用 Microsoft Windows 建立多執行緒應用程式的支援  
  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)  
 描述處理序和執行序，以及進行多執行緒處理的 MFC 方法。  
  
 [多執行緒和地區設定](../../parallel/multithreading-and-locales.md)  
 討論在多執行緒應用程式中，使用 C 執行階段程式庫和 Standard C\+\+ 程式庫的地區設定功能時所發生的問題。  
  
## 相關章節  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
 代表應用程式內執行的執行緒。  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
 描述一個純虛擬類別，可提供 Win32 中同步物件 \(Synchronization Object\) 常見的功能。  
  
 [CSemaphore](../../mfc/reference/csemaphore-class.md)  
 代表號誌 \(Semaphore\)，即是允許限定數量的執行緒在一或多個處理序中存取資源的同步物件。  
  
 [CMutex](../../mfc/reference/cmutex-class.md)  
 代表 Mutex，即允許執行緒互斥 \(Mutually Exclusive\) 存取資源的同步物件。  
  
 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)  
 代表關鍵區段 \(Critical Section\)，即是一次允許一個執行緒存取資源或程式碼區段的同步物件。  
  
 [CEvent](../../mfc/reference/cevent-class.md)  
 代表事件，即是允許一個執行緒通知另一個執行緒事件已經發生的同步物件。  
  
 [CMultiLock](../../mfc/reference/cmultilock-class.md)  
 代表多執行緒程式用來控制多個資源存取的存取控制機制。  
  
 [CSingleLock](../../mfc/reference/csinglelock-class.md)  
 代表多執行緒程式用來控制單一資源存取的存取控制機制。  
  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/zh-tw/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 提供主題連結，這些主題將描述 Visual C\+\+ 程式庫的概念性資訊，以及討論各種程式碼撰寫技術和技巧。