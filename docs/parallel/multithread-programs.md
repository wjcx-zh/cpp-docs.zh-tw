---
title: "多執行緒程式 | Microsoft Docs"
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
  - "多執行緒 [C++], 關於執行緒"
  - "執行緒 [C++], 關於執行緒"
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行緒基本上是一個經由程式的執行路徑。  它也是 Win32 排程執行的最小單位。  執行緒由堆疊、CPU 暫存器的狀態和系統排程器之執行清單裡的項目所組成。  每個執行緒共用所有處理序的資源。  
  
 處理序由一或多個執行緒和程式碼、資料以及程式在記憶體中的其他資源所組成。  一般的程式資源是開啟檔案、號誌 \(Semaphore\) 和動態配置的記憶體。  當系統排程器給與一個執行緒執行控制權，程式就會執行。  排程器決定哪些執行緒要執行以及何時執行。  當較高優先權執行緒在完成工作時，優先權較低的執行緒可能必須等待。  在多處理器的電腦上，排程器可以將各個執行緒移到不同的處理器上來平衡 CPU 的負載。  
  
 在處理序中每一個執行緒都獨立作業。  除非您讓它們彼此看得見對方，否則執行緒是個別執行而且不知道處理序 \(Process\) 裡有其他執行緒存在。  然而，共用通用資源的執行緒必須藉著使用號誌或其他處理序之間的通訊方法來協調。  如需同步處理執行緒的詳細資訊，請參閱[撰寫多執行緒 Win32 程式](../parallel/writing-a-multithreaded-win32-program.md)。  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)