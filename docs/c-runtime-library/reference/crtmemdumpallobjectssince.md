---
title: "_CrtMemDumpAllObjectsSince | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemDumpAllObjectsSince"
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
  - "CrtMemDumpAllObjectsSince"
  - "_CrtMemDumpAllObjectsSince"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtMemDumpAllObjectsSince 函式"
  - "CrtMemDumpAllObjectsSince 函式"
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtMemDumpAllObjectsSince
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如需物件的傾印資訊在堆積從啟動程式執行或從指定的堆積狀態 \(僅偵錯版本\)。  
  
## 語法  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### 參數  
 `state`  
 對堆積狀態開始傾印從或 **NULL**的指標。  
  
## 備註  
 `_CrtMemDumpAllObjectsSince` 函式在堆積傾印物件配置偵錯標頭資訊以使用者可閱讀的格式。  傾印資訊可以由應用程式追蹤組態和偵測記憶體問題時使用。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtMemDumpAllObjectsSince` 的呼叫將被移除。  
  
 `_CrtMemDumpAllObjectsSince` 在何處使用 `state` 參數的值會判斷啟始傾印作業。  若要啟動傾印從指定的堆積狀態， `state` 參數必須是指標到由 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 已填入的 **\_CrtMemState** 結構，在呼叫 `_CrtMemDumpAllObjectsSince` 之前。  當 `state` 為 **NULL**時，函式從頭開始傾印程式執行。  
  
 如果應用程式藉由呼叫 [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md)安裝傾印攔截函式，則每次 `_CrtMemDumpAllObjectsSince` 傾印區塊 `_CLIENT_BLOCK` 型別的資訊，它會呼叫由應用程式所提供的傾印函式。  根據預設，內部 C 執行階段區塊 \(`_CRT_BLOCK`\) 不包含在記憶體傾印作業。  [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式可用來將 `_CRTDBG_CHECK_CRT_DF` 位元 **\_crtDbgFlag** \(包括這些區塊\)。  此外，如釋放或忽略標記的區塊 \(**\_FREE\_BLOCK**， **\_IGNORE\_BLOCK**\) 在記憶體傾印不包含。  
  
 如需堆積狀態的函式和 `_CrtMemState` 結構的詳細資訊，請參閱 [堆積狀態報告函式](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的更多詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**\_CrtMemDumpAll\-ObjectsSince**|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 如需範例 `_CrtMemDumpAllObjectsSince`使用方式，請參閱 [crt\_dbg2](http://msdn.microsoft.com/zh-tw/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)