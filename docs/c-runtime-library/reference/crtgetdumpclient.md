---
title: "_CrtGetDumpClient | Microsoft Docs"
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
  - "_CrtGetDumpClient"
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
  - "CrtGetDumpClient"
  - "_CrtGetDumpClient"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtGetDumpClient 函式"
  - "CrtGetDumpClient 函式"
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtGetDumpClient
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取傾印 `_CLIENT_BLOCK` 型別記憶體區塊的目前應用程式定義之函式 \(僅偵錯版本\)。  
  
## 語法  
  
```  
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );  
```  
  
## 傳回值  
 傳回目前傾印常式。  
  
## 備註  
 `_CrtGetDumpClient` 函式擷取傾印的執行階段 C 的 `_CLIENT_BLOCK` 記憶體區塊儲存物件的目前攔截函式偵錯記憶體傾印流程。  
  
 如需使用其他攔截功能的執行階段函式，以及撰寫自己的用戶端定義攔截函式的詳細資訊，請參閱 [撰寫偵錯攔截函式](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtGetDumpClient`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md)