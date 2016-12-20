---
title: "_rmtmp | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_rmtmp"
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
  - "rmtmp"
  - "_rmtmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_rmtmp 函式"
  - "檔案 [C++], 移除"
  - "檔案 [C++], 暫存"
  - "移除暫存檔案"
  - "rmtmp 函式"
  - "暫存檔案 [C++], 移除"
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rmtmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除暫存檔案。  
  
## 語法  
  
```  
  
int _rmtmp( void );  
```  
  
## 傳回值  
 `_rmtmp` 會關閉和刪除之暫存檔案的數目。  
  
## 備註  
 `_rmtmp` 函式清除在目前目錄中的所有暫存檔。  函式刪除 `tmpfile`建立的那些檔案;只能在暫存檔案建立的相同目錄中。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_rmtmp`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 請參閱 [tmpfile](../../c-runtime-library/reference/tmpfile.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)