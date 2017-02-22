---
title: "_CrtMemDumpStatistics | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemDumpStatistics"
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
  - "CrtMemDumpStatistics"
  - "_CrtMemDumpStatistics"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtMemDumpStatistics 函式"
  - "CrtMemDumpStatistics 函式"
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _CrtMemDumpStatistics
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對採用使用者可讀格式的指定堆積狀態，傾印偵錯標頭資訊 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void _CrtMemDumpStatistics(   
   const _CrtMemState *state   
);  
```  
  
#### 參數  
 `state`  
 要傾印的堆積狀態指標。  
  
## 備註  
 `_CrtMemDumpStatistics` 函式會針對採用使用者可讀格式的指定堆積狀態，傾印偵錯標頭資訊。 應用程式會使用此傾印統計資料追蹤配置及偵測記憶體問題。 記憶體狀態可能包含特定堆積狀態或兩個狀態之間的差異。 未定義 [\_DEBUG](../../c-runtime-library/debug.md) 時，會在前置處理期間移除 `_CrtMemDumpStatistics` 的呼叫。  
  
 `state` 參數必須是指向 `_CrtMemState` 結構的指標，該結構已由 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填入或由 [\_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md) 傳回再呼叫 `_CrtMemDumpStatistics`。 如果 `state` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，而且不會採取任何動作。 如需詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如需堆積狀態函式和 `_CrtMemState` 結構的詳細資訊，請參閱[Heap State Reporting Functions](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。 如需在偵錯版本的基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_CrtMemDumpStatistics`|\<crtdbg.h\>|\<errno.h\>|  
  
 如需詳細的相容性資訊，請參閱簡介中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 <xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName>  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)