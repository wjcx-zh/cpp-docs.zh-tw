---
title: "_lock_file | Microsoft Docs"
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
  - "_lock_file"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_lock_file"
  - "lock_file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lock_file 函式"
  - "檔案鎖定 [C++]"
  - "lock_file 函式"
ms.assetid: 75c7e0e6-efff-4747-b6ed-9bcf2b0894c3
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lock_file
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

鎖定 `FILE` 物件確保並行存取 `FILE` 物件的執行緒的一致性。  
  
## 語法  
  
```  
void _lock_file(  
   FILE* file  
);  
```  
  
#### 參數  
 `file`  
 檔案控制代碼。  
  
## 備註  
 `_lock_file` 函式鎖定 `file`指定的 `FILE` 物件。  基礎檔案未由 `_lock_file`鎖定。  使用 [\_unlock\_file](../../c-runtime-library/reference/unlock-file.md) 釋放在檔案的鎖定。  在執行緒必須與呼叫 `_lock_file` 和 `_unlock_file` 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lock_file`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_lock_file.c  
// This example creates multiple threads that write to standard output  
// concurrently, first with _file_lock, then without.  
  
#include <stdio.h>  
#include <process.h>// _beginthread  
#include <windows.h>// HANDLE  
  
void Task_locked( void* str )  
{  
    for( int i=0; i<1000; ++i )  
    {  
        _lock_file( stdout );  
        for( char* cp = (char*)str; *cp; ++cp )  
        {  
            _fputc_nolock( *cp, stdout );  
        }  
        _unlock_file( stdout );  
    }  
}  
  
void Task_unlocked( void* str )  
{  
    for( int i=0; i<1000; ++i )  
    {  
        for( char* cp = (char*)str; *cp; ++cp )  
        {  
            fputc( *cp, stdout );  
        }  
    }  
}  
  
int main()  
{  
    HANDLE h[3];  
    h[0] = (HANDLE)_beginthread( &Task_locked, 0, "First\n" );  
    h[1] = (HANDLE)_beginthread( &Task_locked, 0, "Second\n" );  
    h[2] = (HANDLE)_beginthread( &Task_locked, 0, "Third\n" );  
  
    WaitForMultipleObjects( 3, h, true, INFINITE );  
  
    h[0] = (HANDLE)_beginthread( &Task_unlocked, 0, "First\n" );  
    h[1] = (HANDLE)_beginthread( &Task_unlocked, 0, "Second\n" );  
    h[2] = (HANDLE)_beginthread( &Task_unlocked, 0, "Third\n" );  
  
    WaitForMultipleObjects( 3, h, true, INFINITE );  
}  
```  
  
  **...**  
**First**  
**秒**  
**First**  
**秒**  
**第三個**  
**秒**  
**第三個**  
**秒**  
**...**  
**FSiercsotn**  
**dF**  
**iSrescto**  
**nFdi**  
**rSsetc**  
**oFnidr**  
**sSte**  
**cFoinrds**  
**tS**  
**eFciornsdt**   
## .NET Framework 對等用法  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_unlock\_file](../../c-runtime-library/reference/unlock-file.md)