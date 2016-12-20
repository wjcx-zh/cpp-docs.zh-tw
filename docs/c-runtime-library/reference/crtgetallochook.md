---
title: "_CrtGetAllocHook | Microsoft Docs"
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
  - "_CrtGetAllocHook"
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
  - "CrtGetAllocHook"
  - "_CrtGetAllocHook"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtGetAllocHook 函式"
  - "CrtGetAllocHook 函式"
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtGetAllocHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取目前用於掛鈎至 C 執行階段偵錯記憶體配置處理程序的客戶自定義配置函式 \(僅限偵錯版本\)。  
  
## 語法  
  
```  
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );  
```  
  
## 傳回值  
 回傳目前定義的掛鈎配置函式  
  
## 備註  
 `_CrtGetAllocHook` 擷取目前 C 執行階段偵錯程式庫記憶體配置處理程序的使用者自定義應用程式掛鈎函式。  
  
 如需使用其他攔截功能的執行階段函式，以及撰寫自己的用戶端定義攔截函式的詳細資訊，請參閱 [撰寫偵錯攔截函式](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtGetAllocHook`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtSetAllocHook](../../c-runtime-library/reference/crtsetallochook.md)