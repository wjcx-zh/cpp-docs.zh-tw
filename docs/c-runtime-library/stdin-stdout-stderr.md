---
title: "stdin、stdout、stderr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdin"
  - "stderr"
  - "stdout"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "標準錯誤資料流"
  - "標準輸入資料流"
  - "標準輸出資料流"
  - "stderr 函式"
  - "stdin 函式"
  - "stdout 函式"
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# stdin、stdout、stderr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## 備註  
 這些是輸入、輸出和錯誤輸出的標準資料流。  
  
 根據預設，標準輸出和標準錯誤列印至螢幕，標準輸入從鍵盤讀取。  
  
 下列資料流指標可存取標準資料流:  
  
|指標|資料流|  
|--------|---------|  
|`stdin`|標準輸入|  
|**stdout**|標準輸出|  
|`stderr`|標準錯誤|  
  
 這些指標可以用來做為函式的引數。  某些功能，例如 **getchar** 和 `putchar`，就會自動使用 `stdin` 和 **stdout** 。  
  
 這些指標是常數，且無法指派新的值。  `freopen` 函式可以重新導向資料流到磁碟檔案或其他裝置。  作業系統可讓您變更程式的標準輸入和輸出導向在命令陣序。  
  
## 請參閱  
 [資料流 I\/O](../c-runtime-library/stream-i-o.md)   
 [全域常數](../c-runtime-library/global-constants.md)