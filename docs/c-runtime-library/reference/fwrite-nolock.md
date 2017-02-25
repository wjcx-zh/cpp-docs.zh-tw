---
title: "_fwrite_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fwrite_nolock"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_fwrite_nolock"
  - "fwrite_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fwrite_nolock 函式"
  - "fwrite_nolock 函式"
  - "資料流, 寫入資料目標"
ms.assetid: 2b4ec6ce-742e-4615-8407-44a0a18ec1d7
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _fwrite_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫入資料至資料流，而不用鎖定的執行緒。  
  
## 語法  
  
```  
size_t _fwrite_nolock(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 參數  
 `buffer`  
 要寫入之資料的指標。  
  
 `size`  
 項目大小 \(以位元組為單位\)。  
  
 `count`  
 要寫入的最大項目數。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## 傳回值  
 與 [fwrite](../../c-runtime-library/reference/fwrite.md) 相同。  
  
## 備註  
 這個函式是 `fwrite`的非鎖定版本。  它與 `fwrite` 是相同的，但它不會防止其他執行緒的干擾。  因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fwrite_nolock`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 請參閱 [fread](../../c-runtime-library/reference/fread.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_write](../../c-runtime-library/reference/write.md)