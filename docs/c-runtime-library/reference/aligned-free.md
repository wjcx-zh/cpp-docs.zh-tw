---
title: "_aligned_free | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_free"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "aligned_free"
  - "_aligned_free"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_free 函式"
  - "aligned_free 函式"
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _aligned_free
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放先前用 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 分配的記憶體區塊。  
  
## 語法  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### 參數  
 `memblock`  
 傳回至 `_aligned_malloc` 或 `_aligned_offset_malloc` 函式的記憶體區塊的指標。  
  
## 備註  
 `_aligned_free` 標記為 `__declspec(noalias)`，表示函式保證不會修改全域變數。  如需詳細資訊，請參閱[noalias](../../cpp/noalias.md)。  
  
 這個函式不會驗證其參數，不同於其他 \_aligned CRT 函式。  如果 `memblock` 是 `NULL` 指標，這個函式不會執行任何動作。  它不會變更 `errno` ，也不叫用無效的參數處理常式。  如果函式因為發生不使用 \_aligned 函式配置的記憶體區塊或由於某些無法預料的嚴重事件而記憶體不重合，函式會從 [\_RPT、\_RPTF、\_RPTW、\_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 產生偵錯報告。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_free`|\<malloc.h\>|  
  
## 範例  
 如需詳細資訊，請參閱 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)