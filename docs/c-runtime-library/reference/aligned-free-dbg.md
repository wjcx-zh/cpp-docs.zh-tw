---
title: "_aligned_free_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_aligned_free_dbg"
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
  - "_aligned_free_dbg"
  - "aligned_free_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_aligned_free_dbg 函式"
  - "aligned_free_dbg 函式"
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _aligned_free_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放使用 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊 \(僅限偵錯\)。  
  
## 語法  
  
```  
void _aligned_free_dbg(    void *memblock );  
```  
  
#### 參數  
 `memblock`  
 傳回 `_aligned_malloc` 或 `_aligned_offset_malloc` 函式之記憶體區塊的指標。  
  
## 備註  
 `_aligned_free_dbg`  函式是偵錯版本的 [\_aligned\_free](../../c-runtime-library/reference/aligned-free.md) 函式。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，每個 `_aligned_free_dbg` 的呼叫會降至 \_`aligned_free` 的呼叫。  \_`aligned_free` 和 `_aligned_free_dbg` 都會釋放基底堆積中的記憶體區塊，但 `_aligned_free_dbg`  還容納偵錯功能：將釋放的記憶體區塊保留在堆積的連結清單中以模擬低記憶體狀況。  
  
 `_aligned_free_dbg` 會先對所有指定檔案和區塊位置執行有效性檢查，再執行釋放作業。  應用程式不需要提供此資訊。  釋放記憶體區塊時，偵錯堆積管理員會自動檢查使用者部分每一端的緩衝區完整性，並在發生覆寫時發出錯誤報表。  若設定 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的 `_CRTDBG_DELAY_FREE_MEM_DF`  位元欄位，會將釋放的區塊填入值 0xDD，並指派 `_FREE_BLOCK` 區塊類型，且會保留在記憶體區塊的堆積的連結清單中。  
  
 若釋放記憶體發生錯誤，會使用來自作業系統且具有失敗性質的資訊設定 `errno`。  如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型以及如何使用它們的詳細資訊，請參閱[偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需在應用程式的偵錯組建中呼叫標準堆積函式以及其偵錯版本之間的差異的資訊，請參閱[堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_aligned_free_dbg`|\<crtdbg.h\>|  
  
 如需相容性詳細資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)