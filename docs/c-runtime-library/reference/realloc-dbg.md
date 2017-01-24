---
title: "_realloc_dbg | Microsoft Docs"
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
  - "_realloc_dbg"
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
apitype: "DLLExport"
f1_keywords: 
  - "_realloc_dbg"
  - "realloc_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "重新配置記憶體區塊"
  - "realloc_dbg 函式"
  - "記憶體區塊, 重新配置"
  - "記憶體, 重新配置"
  - "_realloc_dbg 函式"
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _realloc_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移動及\/或調整區塊以在堆積中重新配置指定的記憶體區塊 \(僅偵錯版本\)。  
  
## 語法  
  
```  
void *_realloc_dbg(  
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### 參數  
 `userData`  
 指向先前配置的記憶體區塊的指標。  
  
 `newSize`  
 重新配置區塊 \(位元組\) 要求的大小。  
  
 `blockType`  
 重新配置區塊所要求的型別：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向要求 `realloc` 作業的來源檔案名稱或 null 之指標。  
  
 `linenumber`  
 `realloc` 作業為要求或空的原始程式檔行號。  
  
 `filename` 和 `linenumber` 參數只有在 `_realloc_dbg` 已經明確呼叫或 [\_CRTDBG\_MAP\_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) 前置處理器常數已經被定義後才可使用。  
  
## 傳回值  
 在成功完成後，這個函式會傳回指向重新配置的記憶體區塊的使用者部分的指標、呼叫新處理常式函式、或傳回 null。  如需傳回行為的完整說明，請參閱之後的備註章節。  如需使用新處理常式函式的詳細資訊，請參閱 [realloc](../../c-runtime-library/reference/realloc.md) 函式。  
  
## 備註  
 `_realloc_dbg` 是 [realloc](../../c-runtime-library/reference/realloc.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_realloc_dbg` 的每個呼叫會減少為對 `realloc` 的一個呼叫。  `realloc` 和 `_realloc_dbg` 皆在基底堆積重新配置一個記憶體區塊，不過 `_realloc_dbg` 搭載幾個偵錯功能：在使用者部分的區塊內其中一邊的緩衝區，可測試遺漏；可追蹤特定配置型別的區塊類型參數；決定配置要求的原點之 `filename`\/`linenumber` 資訊。  
  
 `_realloc_dbg` 會重新配置給特定的記憶體區塊比要求的 `newSize` 更多空間。  `newSize` 可能大於或小於最初配置的記憶體區塊之大小。  偵錯堆積管理員用額外空間來連接偵錯記憶體區塊，並提供應用程式偵錯標頭資訊並覆寫緩衝區。  重新配置可能會造成原始記憶體區塊移至堆積中的不同位置，以及變更記憶體區塊的大小。  如果記憶體區塊移動，原始區塊的內容會被覆寫。  
  
 如果記憶體配置失敗或者需要的記憶體數量 \(先前提到的包括額外負荷\) 超過 `_HEAP_MAXREQ`，`_realloc_dbg` 會將 `errno` 設至 `ENOMEM`。  如需有關這個錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需呼叫標準堆積函式以及偵錯應用程式的偵錯組建的版本之差異的詳細資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_realloc_dbg`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 請參閱 [\_msize\_dbg](../../c-runtime-library/reference/msize-dbg.md) 主題的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)