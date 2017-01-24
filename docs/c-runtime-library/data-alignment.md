---
title: "資料對齊 | Microsoft Docs"
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
  - "data.alignment"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "資料對齊 [C++]"
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資料對齊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列 C 執行階段函式支援資料對齊。  
  
### 資料對齊常式  
  
|常式|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[\_aligned\_free](../c-runtime-library/reference/aligned-free.md)|釋放先前與 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)的記憶體區塊。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_free\_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|釋放先前用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 分配的記憶體區塊 \(僅限偵錯\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md)|在指定的對齊界限配置記憶體。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_malloc\_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|在指定的對齊界限配置記憶體與偵錯標頭和重新寫入緩衝區的額外空間 \(僅偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_msize](../c-runtime-library/reference/aligned-msize.md)|回傳堆積中分配的記憶體區塊的大小。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_msize\_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|傳回所配置的堆積的記憶體區塊大小 \(僅偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|在指定的對齊界限配置記憶體。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_malloc\_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|在指定的對齊界限內配置記憶體 \(僅限偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|變更 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 配置的記憶體區塊大小。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_realloc\_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|變更 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 配置的記憶體區塊大小\(僅限偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|變更配置與 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 記憶體區塊的大小並初始化記憶體為 0 。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_offset\_recalloc\_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|變更配置與 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 記憶體區塊的大小並初始化記憶體為 0 \(僅偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_realloc](../c-runtime-library/reference/aligned-realloc.md)|變更 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 配置的記憶體區塊大小。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_realloc\_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|變更 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 配置的記憶體區塊大小\(僅限偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|變更配置與 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 記憶體區塊的大小並初始化記憶體為 0 。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_aligned\_recalloc\_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|變更配置與 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) 記憶體區塊的大小並初始化記憶體為 0 \(僅偵錯版本\)。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)