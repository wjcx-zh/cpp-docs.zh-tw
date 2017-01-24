---
title: "unexpected (CRT) | Microsoft Docs"
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
  - "unexpected"
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
  - "unexpected"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "unexpected 函式"
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unexpected (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 `terminate` 或您指定使用 `set_unexpected` 的函式。  
  
## 語法  
  
```  
void unexpected( void );  
```  
  
## 備註  
 `unexpected` 常式沒有使用 C\+\+ 例外狀況處理的目前實作。  根據預設，`unexpected` 會呼叫 `terminate`。  您可以撰寫自訂的的終止函式和以 `set_unexpected` 作為引數呼叫您自訂的函式名稱函數以變更此預設行為。  `unexpected`會呼叫指定的最後一個函式做為 `set_unexpected` 的引數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`unexpected`|\<eh.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Exception Class](https://msdn.microsoft.com/en-us/library/system.exception.aspx)  
  
## 請參閱  
 [例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)