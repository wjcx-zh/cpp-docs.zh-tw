---
title: "_endthread、_endthreadex | Microsoft Docs"
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
  - "_endthread"
  - "_endthreadex"
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
  - "_endthread"
  - "endthreadex"
  - "_endthreadex"
  - "endthread"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_endthread 函式"
  - "endthread 函式"
  - "結束執行緒"
  - "endthreadex 函式"
  - "_endthreadex 函式"
  - "執行緒 [c + +]，結束執行緒"
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _endthread、_endthreadex
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

中止執行緒；`_endthread` 會中止由 `_beginthread` 建立的執行緒，而 `_endthreadex` 會終止由 `_beginthreadex` 建立的執行緒。  
  
## 語法  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### 參數  
 `retval`  
 執行緒結束代碼。  
  
## 備註  
 您可以明確地呼叫 `_endthread` 或 `_endthreadex` 來終止執行緒。不過，當執行緒從作為參數傳遞至 `_endthread` 或 `_endthreadex` 的常式傳回時，也會自動呼叫 `_beginthread` 或 `_beginthreadex`。 透過呼叫 `endthread` 或 `_endthreadex` 終止執行緒，有助於確保適當復原配置給執行緒的資源。  
  
> [!NOTE]
>  對於與 Libcmt.lib 連結的可執行檔，請勿呼叫 Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) 應用程式開發介面，這會阻止執行階段系統回收配置的資源。`_endthread` 和 `_endthreadex` 會回收配置的執行緒資源，然後呼叫 `ExitThread`。  
  
 `_endthread` 會自動關閉執行緒控制代碼。 \(此行為與 Win32 `ExitThread` API 不同\)。 因此，當您使用 `_beginthread` 和 `_endthread` 時，不要藉由呼叫 Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) 應用程式開發介面，明確地關閉執行緒控制代碼。  
  
 像 Win32 `ExitThread` API 一樣，`_endthreadex` 不會關閉執行緒控制代碼。 因此，當您使用 `_beginthreadex` 和 `_endthreadex` 時，您必須呼叫 Win32 `CloseHandle` API，以關閉執行緒控制代碼。  
  
> [!NOTE]
>  `_endthread` 和 `_endthreadex` 會導致在執行緒中暫止的 C\+\+ 解構函式不會被呼叫。  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`_endthread`|\<process.h\>|  
|`_endthreadex`|\<process.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 僅限 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的多執行緒版本。  
  
## 範例  
 請參閱 [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_beginthread、\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)