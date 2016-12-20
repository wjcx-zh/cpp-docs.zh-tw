---
title: "_fflush_nolock | Microsoft Docs"
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
  - "_fflush_nolock"
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
  - "fflush_nolock"
  - "_fflush_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fflush_nolock 函式"
  - "fflush_nolock 函式"
  - "清除"
  - "資料流, 清除"
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fflush_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

清除資料流，而不用鎖定的執行緒。  
  
## 語法  
  
```  
int _fflush_nolock(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 `FILE` 結構的指標。  
  
## 傳回值  
 請參閱 [fflush](../../c-runtime-library/reference/fflush.md)。  
  
## 備註  
 這個函式是 `fflush`的非鎖定版本。  它與 `fflush` 是相同的，但它不會防止其他執行緒的干擾。  因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_fflush_nolock`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [setvbuf](../../c-runtime-library/reference/setvbuf.md)