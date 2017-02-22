---
title: "_free_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_free_dbg"
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
  - "_free_dbg"
  - "free_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "記憶體區塊，解除配置"
  - "釋放記憶體"
  - "_free_dbg 函式"
  - "free_dbg 函式"
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _free_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放在堆積上的記憶體區塊 \(僅偵錯版本\)。  
  
## 語法  
  
```  
void _free_dbg(   
   void *userData,  
   int blockType   
);  
```  
  
#### 參數  
 `userData`  
 要釋放的配置的記憶體區塊的指標。  
  
 `blockType`  
 要釋放的配置的記憶體區塊類型: `_CLIENT_BLOCK`、 `_NORMAL_BLOCK`或 `_IGNORE_BLOCK`。  
  
## 備註  
 `_free_dbg` 函式是 [free](../../c-runtime-library/reference/free.md) 函式的偵錯版本。  當 [\_DEBUG](../../c-runtime-library/debug.md) 未定義時，對 `_free_dbg` 的每個呼叫會減少為對 `free` 的一個呼叫。  `free` 和 `_free_dbg` 釋放在基底堆積的記憶體區塊，不過， `_free_dbg` 容納兩個偵錯功能:能夠保持釋放堆積的連結串列以模擬低記憶體情況和一個區塊類型參數以釋放特定配置類型。  
  
 `_free_dbg` 在執行釋放作業之前執行所有指定之檔案和區塊位置之有效性檢查。  應用程式不應該提供這項資訊。  當記憶體區塊被釋放時，偵錯堆積管理器會自動檢查配置區域每端的使用者部分之完整性，如果發生覆寫發便會發出錯誤報告。  如果 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的 `_CRTDBG_DELAY_FREE_MEM_DF` 位元欄位已設定，釋放的區塊在記憶體區塊填入 0xDD 值，指定 `_FREE_BLOCK` 區塊類型，並保留在記憶體區塊的堆疊連結串列。  
  
 如果錯誤發生在釋放記憶體， `errno` 設定成作業系統發生錯誤的性質的資訊。  如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  如需配置區塊類型的資訊以及它們的使用方式，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  如需呼叫標準堆積函式以及偵錯應用程式的偵錯組建的版本之差異的詳細資訊，請參閱 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_free_dbg`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 如需範例 `_free_dbg`使用方式，請參閱 [crt\_dbg2](http://msdn.microsoft.com/zh-tw/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)