---
title: "_isatty | Microsoft Docs"
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
  - "_isatty"
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
  - "_isatty"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isatty 函式"
  - "字元裝置檢查"
  - "檢查字元裝置"
  - "isatty 函式"
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _isatty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷檔案描述項是否與字元裝置有關聯。  
  
## 語法  
  
```  
  
      int _isatty(  
int fd   
);  
```  
  
#### 參數  
 `fd`  
 參考要測試之裝置的檔案描述項。  
  
## 傳回值  
 如果描述元與字元裝置有關聯，則`_isatty` 會傳回非零的值。  否則，`_isatty` 會傳回 0 。  
  
## 備註  
 `_isatty` 函式會判斷 `fd` 是否與字元裝置 \(終端機、主控台、印表機、序列埠\)。  
  
 這個函式會驗證它的`fd` 參數。  如果 `fd` 為不好的檔案指標，則如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述，會叫用無效參數處理常式。  如果允許繼續執行，則函式會傳回 0 並將 `errno` 設定為 `EBADF`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_isatty`|\<io.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_isatty.c  
/* This program checks to see whether  
 * stdout has been redirected to a file.  
 */  
  
#include <stdio.h>  
#include <io.h>  
  
int main( void )  
{  
   if( _isatty( _fileno( stdout ) ) )  
      printf( "stdout has not been redirected to a file\n" );  
   else  
      printf( "stdout has been redirected to a file\n");  
}  
```  
  
## 範例輸出  
  
```  
stdout has not been redirected to a file  
```  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)