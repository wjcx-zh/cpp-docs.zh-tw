---
title: "_fread_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fread_nolock"
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
  - "_fread_nolock"
  - "fread_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fread_nolock 函式"
  - "資料 [C++], 從輸入資料流讀取"
  - "fread_nolock 函式"
  - "讀取資料 [C++], 從輸入資料流"
  - "資料流 [C++], 讀取資料來源"
ms.assetid: 60e4958b-1097-46f5-a77b-94af5e7dba40
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _fread_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流讀取資料，而不用鎖定其他執行緒。  
  
## 語法  
  
```  
size_t _fread_nolock(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### 參數  
 `buffer`  
 資料儲存位置  
  
 `size`  
 項目大小 \(以位元組為單位\)。  
  
 `count`  
 要讀取的最大項目數。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## 傳回值  
 請參閱 [fread](../../c-runtime-library/reference/fread.md)。  
  
## 備註  
 這個函式是 `fread`的非鎖定版本。  它與 `fread` 是相同的，但它不會防止其他執行緒的干擾。  因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fread_nolock`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [\_read](../../c-runtime-library/reference/read.md)