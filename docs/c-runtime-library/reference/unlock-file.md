---
title: "_unlock_file | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_unlock_file"
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
  - "_unlock_file"
  - "unlock_file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_unlock_file 函式"
  - "檔案 [C++], 解除鎖定"
  - "unlock_file 函式"
  - "解除鎖定檔案"
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# _unlock_file
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟檔案，讓其他處理序存取檔案。  
  
## 語法  
  
```  
void _unlock_file(  
   FILE* file  
);  
```  
  
#### 參數  
 `file`  
 檔案控制代碼。  
  
## 備註  
 `_unlock_file` 函式開啟 `file`指定的檔案。  開啟檔案，讓其他處理序存取檔案。  除非 `_lock_file` 先前已經呼叫 `file` 指標，這個函式不應該呼叫。  呼叫中未鎖定的檔案的 `_unlock_file` 可能會造成死結。  如需範例，請參閱 [\_lock\_file](../../c-runtime-library/reference/lock-file.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_unlock_file`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_lock\_file](../../c-runtime-library/reference/lock-file.md)