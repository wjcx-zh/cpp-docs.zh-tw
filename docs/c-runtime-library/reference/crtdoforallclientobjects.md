---
title: "_CrtDoForAllClientObjects | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtDoForAllClientObjects"
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
  - "_CrtDoForAllClientObjects"
  - "CrtDoForAllClientObjects"
  - "crtdbg/_CrdDoForAllClientObjects"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtDoForAllClientObjects 函式"
  - "CrtDoForAllClientObjects 函式"
ms.assetid: d0fdb835-3cdc-45f1-9a21-54208e8df248
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _CrtDoForAllClientObjects
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對堆積中的所有 `_CLIENT_BLOCK` 類型呼叫應用程式提供的函式 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void _CrtDoForAllClientObjects(   
   void ( * pfn )( void *, void * ),  
   void *context  
);  
```  
  
#### 參數  
 `pfn`  
 應用程式提供的函式回呼函式的指標。 此函式的第一個參數指向資料。 第二個參數是傳遞至 `_CrtDoForAllClientObjects` 呼叫的內容指標。  
  
 `context`  
 要傳遞至應用程式提供之函式的應用程式提供的內容的指標。  
  
## 備註  
 `_CrtDoForAllClientObjects` 函式會在堆積的連結清單中搜尋具有 `_CLIENT_BLOCK` 類型的記憶體區塊，並在找到此類型的區塊時，呼叫應用程式提供的函式。 找到的區塊和 `context` 參數會作為引數傳遞至應用程式提供的函式。 應用程式可以在偵錯期間追蹤特定配置群組，方法是透過明確呼叫偵錯堆積函式以配置記憶體，並為區塊指定分派 `_CLIENT_BLOCK` 區塊類型。 然後就可以分別追蹤這些區塊，並在遺漏偵測期間和記憶體狀態報告期間個別回報這些區塊。  
  
 若 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的　`_CRTDBG_ALLOC_MEM_DF` 位元欄位未開啟，會立即傳回 `_CrtDoForAllClientObjects`。 若未定義 [\_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtDoForAllClientObjects` 的呼叫。  
  
 如需 `_CLIENT_BLOCK` 類型及其他偵錯函式可以如何使用該類型的詳細資訊，請參閱[偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 若 `pfn` 為 `NULL`，將會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 會設為 `EINVAL`，並傳回函式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtDoForAllClientObjects`|\<crtdbg.h\>、\<errno.h\>|  
  
 如需更多的相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限偵錯版的 C 執行階段程式庫。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)   
 [堆積狀態報告函式](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)