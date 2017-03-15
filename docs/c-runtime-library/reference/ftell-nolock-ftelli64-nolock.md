---
title: "_ftell_nolock、_ftelli64_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftelli64_nolock"
  - "_ftell_nolock"
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
  - "_ftelli64_nolock"
  - "ftelli64_nolock"
  - "ftell_nolock"
  - "_ftell_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftell_nolock 函式"
  - "_ftelli64_nolock 函式"
  - "檔案指標 [C++], 取得目前位置"
  - "ftell_nolock 函式"
  - "ftelli64_nolock 函式"
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _ftell_nolock、_ftelli64_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得檔案指標的目前位置，而不用鎖定的執行緒。  
  
## 語法  
  
```  
long _ftell_nolock(   
   FILE *stream   
);  
__int64 _ftelli64_nolock(   
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 以 `FILE` 結構。  
  
## 傳回值  
 與 `ftell` 和 `_ftelli64`。  如需詳細資訊，請參閱[ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)。  
  
## 備註  
 這些函式分別是 `ftell` 和 `_ftelli64`的非鎖定版本。  它們與 `ftell` 和 `_ftelli64` 是相同的，但不會防止由其他執行緒的功能。  因為這些函式不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
## 需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`ftell_nolock`|\<stdio.h\>|\<errno.h\>|  
|`_ftelli64_nolock`|\<stdio.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek、\_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek、\_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [ftell、\_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)