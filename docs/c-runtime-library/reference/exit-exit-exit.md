---
title: "exit, _Exit, _exit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_exit"
  - "exit"
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
  - "Exit"
  - "_exit"
  - "process/exit"
  - "process/_Exit"
  - "stdlib/exit"
  - "stdlib/_Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit 函式"
  - "_exit 函式"
  - "處理序, 終止"
  - "函式呼叫, 終止"
  - "處理序終止, 呼叫"
ms.assetid: b1501fa6-27c2-478c-9e93-cc4fd802a01f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# exit, _Exit, _exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

終止呼叫處理序。`exit` 函式會在清除之後終止該處理序；`_exit` 及 `_Exit` 會立即予以終止。  
  
> [!NOTE]
>  除了測試或偵錯兩種情況之外，請勿使用此方法關閉通用 Windows 平台 \(UWP\) 應用程式或 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 請勿透過程式設計或 UI 兩種方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 如需 Windows 8 及 8.1 應用程式的詳細資訊，請參閱[應用程式生命週期](http://go.microsoft.com/fwlink/?LinkId=262853)。 如需 Windows 10 應用程式的詳細資訊，請參閱 [Windows 10 app 使用方法指南](http://go.microsoft.com/fwlink/p/?linkid=619133)。  
  
## 語法  
  
```  
void exit(   
   int const status   
);  
void _Exit(   
   int const status   
);  
void _exit(   
   int const status   
);  
```  
  
#### 參數  
 `status`  
 結束狀態碼。  
  
## 備註  
 `exit`、`_Exit` 及 `_exit` 函式會終止呼叫處理序。`exit` 函式會呼叫執行緒區域物件的解構函式，接著再以後進先出 \(LIFO\) 順序呼叫 `atexit` 及 `_onexit` 註冊的函式，最後在終止處理序之前，先排清所有檔案緩衝區。`_Exit` 及 `_exit` 函式在終止處理程序時，不會終結執行緒區域物件或終止處理 `atexit` 或 `_onexit` 函式，也不會排清資料流緩衝區。  
  
 雖然 `exit`、`_Exit` 及 `_exit` 呼叫不會傳回值，但仍會將 `status` 的低階層位元組提供給主機環境，或是在處理序結束之後等待呼叫處理序 \(如其存在\)。 通常呼叫端會將 `status` 值設為 0 表示正常結束，或設為其他值表示錯誤。`status` 值可供作業系統批次命令 `ERRORLEVEL` 使用，而且會由下列兩個常數之一代表：`EXIT_SUCCESS` 代表值 0；`EXIT_FAILURE` 代表值 1。  
  
 `exit`、`_Exit`、`_exit`、`quick_exit`、`_cexit` 及 `_c_exit` 函式的行為如下所示。  
  
|函式|描述|  
|--------|--------|  
|`exit`|執行完整的 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|  
|`_Exit`|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|  
|`_exit`|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|  
|`quick_exit`|執行快速 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|  
|`_cexit`|執行完整的 C 程式庫終止程序，然後傳回給呼叫端。 不會終止處理序。|  
|`_c_exit`|執行基本的 C 程序庫終止程序，然後傳回給呼叫端。 不會終止處理序。|  
  
 當您呼叫 `exit`、`_Exit` 或 `_exit` 函式時，任何在呼叫時即已存在之暫存或自動物件的解構函式皆不會予以呼叫。 自動物件會在物件未被宣告成靜態的函式中定義。 暫存物件是編譯器所建立的物件。 若要先呼叫 `exit`、`_Exit` 或 `_exit` 之前先終結自動物件，請明確呼叫該物件的解構函式，如下所示：  
  
```  
myObject.myClass::~myClass();  
```  
  
 請勿使用 `DLL_PROCESS_ATTACH` 從 `DllMain`呼叫 `exit`。 若要結束 `DLLMain` 函式，請從 `DLL_PROCESS_ATTACH` 傳回 `FALSE`。  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`exit`, `_Exit`, `_exit`|\<process.h\> 或 \<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_exit.c // This program returns an exit code of 1. The // error code could be tested in a batch file. #include <stdlib.h> int main( void ) { exit( 1 ); }  
```  
  
## .NET Framework 對等用法  
 [System::Diagnostics::Process::Kill](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_cexit、\_c\_exit](../../c-runtime-library/reference/cexit-c-exit.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [quick\_exit](../../c-runtime-library/reference/quick-exit1.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)