---
title: "_heapadd | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_heapadd"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "heapadd"
  - "_heapadd"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_heapadd 函式"
  - "heapadd 函式"
  - "堆積, 加入記憶體"
  - "記憶體, 加入至堆積"
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _heapadd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將記憶體加入堆積。  
  
> [!IMPORTANT]
>  此函式已被取代。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。  
  
## 語法  
  
```  
int _heapadd(   
   void *memblock,  
   size_t size   
);  
```  
  
#### 參數  
 `memblock`  
 指向堆積記憶體的指標。  
  
 `size`  
 要加入的記憶體大小 \(位元組\)。  
  
## 傳回值  
 若成功，`_heapadd` 會傳回 0；否則此函式會傳回 \-1，並將 `errno` 設為 `ENOSYS`。  
  
 如需此函式與其他傳回碼的詳細資訊，請參閱 [\_doserrno, errno、\_sys\_errlist 及 \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 自 Visual C\+\+ 4.0 版起，基礎堆積結構已移到 C 執行階段程式庫，以支援新的偵錯功能。 因此，所有採用 Win32 API 的平台將不再支援 `_heapadd`。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_heapadd`|\<malloc.h\>|\<errno.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../c-runtime-library/memory-allocation.md)   
 [free](../c-runtime-library/reference/free.md)   
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapmin](../c-runtime-library/reference/heapmin.md)   
 [\_heapset](../c-runtime-library/heapset.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [malloc](../c-runtime-library/reference/malloc.md)   
 [realloc](../c-runtime-library/reference/realloc.md)