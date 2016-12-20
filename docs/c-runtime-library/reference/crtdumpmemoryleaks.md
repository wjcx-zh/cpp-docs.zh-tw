---
title: "_CrtDumpMemoryLeaks | Microsoft Docs"
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
  - "_CrtDumpMemoryLeaks"
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
  - "CRTDBG_LEAK_CHECK_DF"
  - "CRTDBG_CHECK_CRT_DF"
  - "_CRTDBG_LEAK_CHECK_DF"
  - "CrtDumpMemoryLeaks"
  - "_CrtDumpMemoryLeaks"
  - "_CRTDBG_CHECK_CRT_DF"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtDumpMemoryLeaks 函式"
  - "CRTDBG_LEAK_CHECK_DF 巨集"
  - "_CRTDBG_LEAK_CHECK_DF 巨集"
  - "_CrtDumpMemoryLeaks 函式"
  - "CRTDBG_CHECK_CRT_DF 巨集"
  - "_CRTDBG_CHECK_CRT_DF 巨集"
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtDumpMemoryLeaks
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當記憶體遺漏發生時，在偵錯堆積傾印所有記憶體區塊 \(僅偵錯版本\)。  
  
## 語法  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## 傳回值  
 如果找到記憶體遺漏，則 `_CrtDumpMemoryLeaks` 傳回TRUE。  否則，函式會傳回 false。  
  
## 備註  
 `_CrtDumpMemoryLeaks` 函式會判斷自程式執行啟動後記憶體遺漏是否發生。  找到遺漏時，堆積內所有物件的偵錯標頭資訊會傾印為使用者可閱讀的格式。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtDumpMemoryLeaks` 的呼叫將被移除。  
  
 `_CrtDumpMemoryLeaks` 通常會在程序執行結束時被呼叫，以驗證應用程式配置的所有記憶體已經釋放。  藉由開啟 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的 `_CRTDBG_LEAK_CHECK_DF` 位元欄（使用 [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式），可讓此函式在程式結束時自動被呼叫。  
  
 `_CrtDumpMemoryLeaks` 呼叫 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 以取得堆積的目前狀態然後掃描未釋放區塊的狀態。  當遇到一個未被釋放的區塊時， `_CrtDumpMemoryLeaks` 會呼叫 [\_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 以傾印程式開始執行以來，堆積內配置的所有物件之資訊。  
  
 根據預設，內部 C 執行階段區塊 \(`_CRT_BLOCK`\) 不包含在記憶體傾印作業。  [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式可用來開啟 `_crtDbgFlag` 的 `_CRTDBG_CHECK_CRT_DF`，將這些區塊包含至遺漏檢測程序。  
  
 如需堆積狀態的函式和 `_CrtMemState` 結構的詳細資訊，請參閱 [堆積狀態報告函式](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  如需記憶體區塊配置、初始化的方式，並在基底堆積的偵錯版本管理記憶體區塊的更多詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 如需 `_CrtDumpMemoryLeaks` 使用方式的範例，請參閱 [crt\_dbg1](http://msdn.microsoft.com/zh-tw/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)