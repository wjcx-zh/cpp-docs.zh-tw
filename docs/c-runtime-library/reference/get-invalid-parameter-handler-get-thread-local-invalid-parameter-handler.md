---
title: "_get_invalid_parameter_handler _get_thread_local_invalid_parameter_handler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_invalid_parameter_handler"
  - "_get_thread_local_invalid_parameter_handler"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_invalid_parameter_handler"
  - "stdlib/_get_invalid_parameter_handler"
  - "_get_thread_local_invalid_parameter_handler"
  - "stdlib/_get_thread_local_invalid_parameter_handler"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "_get_thread_local_invalid_parameter_handler 函式"
  - "_get_invalid_parameter_handler 函式"
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_invalid_parameter_handler _get_thread_local_invalid_parameter_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得 CRT 偵測到無效的引數時，會呼叫的函式。  
  
## 語法  
  
```  
_invalid_parameter_handler _get_invalid_parameter_handler(void);  
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);  
```  
  
## 傳回值  
 目前已設定的指標無效參數處理常式函式或如果未設定為 null 指標。  
  
## 備註  
 `_get_invalid_parameter_handler` 函式會取得目前已設定全域無效參數處理常式。 如果已不設定任何全域的無效參數處理常式，它會傳回 null 指標。 同樣地， `_get_thread_local_invalid_parameter_handler` 取得目前的執行緒區域不正確的參數處理常式的執行緒呼叫或 null 指標，如果沒有處理常式設定。 如需有關如何設定全域和執行緒區域無效參數處理常式的資訊，請參閱 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。  
  
 傳回不正確的參數處理常式函式指標具有下列類型︰  
  
```c  
typedef void (__cdecl* _invalid_parameter_handler)(  
    wchar_t const*,  
    wchar_t const*,  
    wchar_t const*,   
    unsigned int,  
    uintptr_t  
    );  
```  
  
 無效的參數處理常式的詳細資訊，請參閱在原型 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_invalid_parameter_handler`, `_get_thread_local_invalid_parameter_handler`|C: \< stdlib.h \><br /><br /> C \+ \+: \< d l i b \> 或 \< stdlib.h \>|  
  
 `_get_invalid_parameter_handler` 和 `_get_thread_local_invalid_parameter_handler` 函式是 Microsoft 專有的。 相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)   
 [CRT 函式的安全性增強版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)