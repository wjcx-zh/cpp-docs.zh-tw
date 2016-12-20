---
title: "_getmaxstdio | Microsoft Docs"
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
  - "_getmaxstdio"
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
  - "_getmaxstdio"
  - "getmaxstdio"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getmaxstdio 函式"
  - "檔案 [C++], 開啟數目"
  - "getmaxstdio 函式"
  - "開啟檔案, 取得編號"
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getmaxstdio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回在資料流 I\/O 層級中允許的同時開啟的檔案數目。  
  
## 語法  
  
```  
int _getmaxstdio( void );  
```  
  
## 傳回值  
 傳回表示同時開啟檔案數目目前允許在 `stdio` 層級的數字。  
  
## 備註  
 使用 [\_setmaxstdio](../../c-runtime-library/reference/setmaxstdio.md) 同時設定開啟檔案數目允許在 `stdio` 層級。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getmaxstdio`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_setmaxstdio.c  
// The program retrieves the maximum number  
// of open files and prints the results  
// to the console.  
  
#include <stdio.h>  
  
int main()  
{  
   printf( "%d\n", _getmaxstdio());  
  
   _setmaxstdio(2048);  
  
   printf( "%d\n", _getmaxstdio());  
}  
```  
  
  **512**  
**2048**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)