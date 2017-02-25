---
title: "_CrtDbgBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtDbgBreak"
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
  - "_CrtDbgBreak"
  - "CrtDbgBreak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgBreak 函式"
  - "CrtDbgBreak 函式"
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _CrtDbgBreak
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在程式碼的某一行設置中斷點。\(請僅在偵錯模式使用。\)  
  
## 語法  
  
```  
void _CrtDbgBreak( void );  
```  
  
## 傳回值  
 沒有傳回值。  
  
## 備註  
 `_CrtDbgBreak` 函式為函式所在的程式碼行設置偵錯中斷點。  此函式必須在偵錯模式下使用且依賴 `_DEBUG` 的預定義。  
  
 如需使用其他攔截功能的執行階段函式和撰寫自己的用戶端定義的攔截函式的詳細資訊，請參閱 [Writing Your Own Debug Hook Functions](../Topic/Debug%20Hook%20Function%20Writing.md) 。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtDbgBreak`|\<CRTDBG.h\>|  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_\_debugbreak](../../intrinsics/debugbreak.md)