---
title: "_cexit、_c_exit | Microsoft Docs"
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
  - "_c_exit"
  - "_cexit"
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
  - "_cexit"
  - "c_exit"
  - "_c_exit"
  - "cexit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_c_exit 函式"
  - "_cexit 函式"
  - "c_exit 函式"
  - "cexit 函式"
  - "處理序期間清除作業"
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cexit、_c_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行清除作業並傳回，而不需要終止處理序。  
  
## 語法  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## 備註  
 `_cexit` 函式會以後進先出 \(LIFO\) 的順序呼叫 `atexit` 和 `_onexit` 註冊的函式。  然後 `_cexit` 清除任何 I\/O 緩衝區並在傳回之前關閉所有開啟的資料流。  `_c_exit` 和 `_exit` 相似，但是傳回至呼叫程序時未處理 `atexit` 或 `_onexit` 或清除資料流緩衝區。  `exit`，`_exit`，`_cexit` 和  `_c_exit` 的行為如下表所示。  
  
|功能|行為|  
|--------|--------|  
|`exit`|執行完成 C 程式庫結束程序，終止處理序，然後用提供的狀態碼關閉。|  
|`_exit`|執行快速 C 程式庫結束程序，終止處理序，然後用提供的狀態碼關閉。|  
|`_cexit`|執行完成 C 程式庫結束程序並傳回至呼叫端，但是不會結束處理序。|  
|`_c_exit`|執行快速 C 程式庫結束程序並傳回至呼叫端，但是不會結束處理序。|  
  
 當您呼叫 `_cexit` 或 `_c_exit` 函式時，呼叫存在的任何暫時或自動物件的解構函式不會呼叫。  自動物件被定義為一個物件未被宣告靜態的函式。  暫存物件是由編譯器所建立的物件。  若要終結自動物件，在呼叫 `_cexit` 或 `_c_exit`之前，請明確地呼叫物件的解構函式，如下所示：  
  
```  
myObject.myClass::~myClass( );  
```  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_cexit`|\<process.h\>|  
|`_c_exit`|\<process.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 [System::Diagnostics::Process::CloseMainWindow](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit，\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn、\_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)