---
title: "_CrtMemCheckpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemCheckpoint"
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
  - "CrtMemCheckpoint"
  - "_CrtMemCheckpoint"
  - "crtdbg/_CrtMemCheckpoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtMemCheckpoint 函式"
  - "_CrtMemCheckpoint 函式"
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _CrtMemCheckpoint
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得偵錯堆積的目前狀態，並儲存在應用程式提供的 `_CrtMemState` 結構中 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
void _CrtMemCheckpoint(  
   _CrtMemState *state   
);  
```  
  
#### 參數  
 `state`  
 指向 `_CrtMemState` 結構以填入記憶體檢查點。  
  
## 備註  
 `_CrtMemCheckpoint` 函式會建立任何指定時間之偵錯堆積目前狀態的快照。 其他堆積狀態函式 \(例如 [\_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)\) 可使用此快照協助偵測記憶體流失及其他問題。 若未定義 [\_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtMemState` 的呼叫。  
  
 應用程式必須將指標傳遞至先前配置之 `_CrtMemState` 結構的執行個體，其定義在 Crtdbg.h 的 `state` 參數中。 如果 `_CrtMemCheckpoint` 在檢查點建立期間遇到錯誤，函式會產生描述問題的 `_CRT_WARN` 偵錯報告。  
  
 如需堆積狀態函式及 `_CrtMemState` 結構的詳細資訊，請參閱[堆積狀態報告函式](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 若 `state` 為 `NULL`，將會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 會設為 `EINVAL`，並傳回函式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtMemCheckpoint`|\<crtdbg.h\>、\<errno.h\>|  
  
 如需更多的相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限 UCRT 的偵錯版本。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtMemDifference](../../c-runtime-library/reference/crtmemdifference.md)