---
title: "_getpid | Microsoft Docs"
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
  - "_getpid"
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
  - "_getpid"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "getpid 函式"
  - "_getpid 函式"
  - "處理序識別碼"
ms.assetid: d3e13bae-9a0c-4f33-86d3-ec9df9519285
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getpid
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得處理序識別碼。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _getpid( void );  
```  
  
## 傳回值  
 傳回從系統取得的處理序 ID。 不會傳回錯誤。  
  
## 備註  
 `_getpid` 函式可從系統取得處理序 ID。 處理序 ID 可唯一識別呼叫處理序。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getpid`|\<process.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_getpid.c  
// This program uses _getpid to obtain  
// the process ID and then prints the ID.  
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
   // If run from command line, shows different ID for   
   // command line than for operating system shell.  
  
   printf( "Process id: %d\n", _getpid() );  
}  
```  
  
```Output  
處理序 ID：3584  
```  
  
## .NET Framework 對等用法  
 [System::Diagnostics::Process::Id](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_mktemp、\_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)