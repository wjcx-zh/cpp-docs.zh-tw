---
title: "_CrtGetReportHook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtGetReportHook"
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
  - "CrtGetReportHook"
  - "_CrtGetReportHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CrtGetReportHook 函式"
  - "_CrtGetReportHook 函式"
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtGetReportHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取攔截它用戶端定義的報告函式進入偵錯報告流程的 C 執行階段 \(僅偵錯版本\)。  
  
## 語法  
  
```  
_CRT_REPORT_HOOK _CrtGetReportHook( void );  
```  
  
## 傳回值  
 傳回目前的用戶端定義報告函式。  
  
## 備註  
 `_CrtGetReportHook` 可讓應用程式擷取執行階段 C 的目前報告函式偵錯程式庫報告流程。  
  
 如需使用其他攔截功能的執行階段函式，以及撰寫自己的用戶端定義攔截函式的詳細資訊，請參閱 [撰寫偵錯攔截函式](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtGetReportHook`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 範例  
 如需 `_CrtSetReportHook`使用方式的範例，請參閱 [報表](http://msdn.microsoft.com/zh-tw/f6e08c30-6bd9-459a-830a-56deec0d2051)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md)