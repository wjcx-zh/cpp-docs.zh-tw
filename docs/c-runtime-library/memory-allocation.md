---
title: "記憶體配置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.memory"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "記憶體配置, 常式"
  - "記憶體, 配置"
  - "記憶體, 管理"
ms.assetid: b4470556-a128-4782-9943-2ccf7a7d9979
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 記憶體配置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這些常式配置、釋放及重新配置記憶體。  
  
### 記憶體配置常式  
  
|常式|用法|.NET Framework 同等|  
|--------|--------|-----------------------|  
|[\_alloca](../c-runtime-library/reference/alloca.md), [\_malloca](../c-runtime-library/reference/malloca.md)|配置堆疊的記憶體|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[calloc](../c-runtime-library/reference/calloc.md)|配置陣列的記憶體，將配置的區塊中的每個位元組初始化為 0|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_calloc\_dbg](../c-runtime-library/reference/calloc-dbg.md)|偵錯版本的 `calloc`；僅適用於偵錯版本的執行階段程式庫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[operator delete](../c-runtime-library/operator-delete-crt.md)|釋放配置的區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[operator delete&#91;&#93;](../c-runtime-library/delete-operator-crt.md)|釋放配置的區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_expand](../c-runtime-library/reference/expand.md)|以不移動的方式展開或壓縮記憶體區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_expand\_dbg](../c-runtime-library/reference/expand-dbg.md)|偵錯版本的 `_expand`；僅適用於偵錯版本的執行階段程式庫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[free](../c-runtime-library/reference/free.md)|釋放配置的區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_free\_dbg](../c-runtime-library/reference/free-dbg.md)|偵錯版本的 `free`；僅適用於偵錯版本的執行階段程式庫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_freea](../c-runtime-library/reference/freea.md)|從堆疊釋放配置的區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_get\_heap\_handle](../c-runtime-library/reference/get-heap-handle.md)|取得 CRT 堆積的 Win32 HANDLE|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapadd](../c-runtime-library/heapadd.md)|將記憶體加入堆積|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapchk](../c-runtime-library/reference/heapchk.md)|檢查堆積的一致性|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapmin](../c-runtime-library/reference/heapmin.md)|釋放堆積中未使用的記憶體|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapset](../c-runtime-library/heapset.md)|使用指定的值填寫釋放堆積項目|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_heapwalk](../c-runtime-library/reference/heapwalk.md)|傳回堆積中每個項目的資訊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[malloc](../c-runtime-library/reference/malloc.md)|配置堆積中的記憶體區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md)|偵錯版本的 `malloc`；僅適用於偵錯版本的執行階段程式庫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_msize](../c-runtime-library/reference/msize.md)|傳回配置的區塊大小|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_msize\_dbg](../c-runtime-library/reference/msize-dbg.md)|偵錯版本的 `_msize`；僅適用於偵錯版本的執行階段程式庫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[new](../c-runtime-library/operator-new-crt.md)|配置堆積中的記憶體區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[new&#91;&#93;](../c-runtime-library/new-operator-crt.md)|配置堆積中的記憶體區塊|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_query\_new\_handler](../c-runtime-library/reference/query-new-handler.md)|傳回 `_set_new_handler` 所設定之目前新處理常式的位址|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_query\_new\_mode](../c-runtime-library/reference/query-new-mode.md)|傳回整數，此整數表示 `_set_new_mode`  為 `malloc` 所設定的新處理常式模式。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[realloc](../c-runtime-library/reference/realloc.md)|將區塊重新配置為新的大小|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_realloc\_dbg](../c-runtime-library/reference/realloc-dbg.md)|偵錯版本的 `realloc`；僅適用於偵錯版本的執行階段程式庫|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)|當 `new` 運算子 \(為了配置記憶體\) 失敗時，啟用錯誤處理機制，並啟用標準範本程式庫 \(STL\) 的編譯。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_set\_new\_mode](../c-runtime-library/reference/set-new-mode.md)|為 `malloc` 設定新處理常式模式|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)