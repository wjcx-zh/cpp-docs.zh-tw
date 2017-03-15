---
title: "_lseek、_lseeki64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lseeki64"
  - "_lseek"
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
  - "_lseeki64"
  - "_lseek"
  - "lseeki64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_lseek 函式"
  - "_lseeki64 函式"
  - "檔案指標 [C++], 移動"
  - "lseek 函式"
  - "lseeki64 函式"
  - "搜尋檔案指標"
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _lseek、_lseeki64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移動檔案指標至指定的位置。  
  
## 語法  
  
```  
  
      long _lseek(  
   int fd,  
   long offset,  
   int origin   
);  
__int64 _lseeki64(  
   int fd,  
   __int64 offset,  
   int origin   
);  
```  
  
#### 參數  
 `fd`  
 參考開啟檔案的檔案描述項。  
  
 *位移*  
 位元組數從 *來源的*。  
  
 *原點*  
 初始位置。  
  
## 傳回值  
 `_lseek` 傳回的位移，以位元組為單位\)，則從檔案的開頭。  `_lseeki64` 會在 64 位元整數的位移。  函式會傳回 1L 表示錯誤。  如果傳遞無效的參數，例如錯誤的檔案描述項或 *原始* 值無效或 *位移來* 指定的位置是，在檔案的一開始，無效的參數處理常式被叫用之前，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EBADF`，並傳回 \-1L。  在裝置上不能達到尋找 \(例如終端和印表機\)，傳回值為 undefined。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_lseek` 函式移動檔案指標與 `fd` 從*原點*開始*位移*位元組的新位置。  檔案中的下一個作業會在新位置時發生。  *原點* 引數必須是下列其中一個常數，在 Stdio.h 定義。  
  
 `SEEK_SET`  
 檔案的開頭。  
  
 `SEEK_CUR`  
 檔案指標目前的位置  
  
 `SEEK_END`  
 檔案結尾。  
  
 您可以使用 `_lseek` 重新定位指標任何檔案或在檔案的結尾。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_lseek`|\<io.h\>|  
|`_lseeki64`|\<io.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_lseek.c  
/* This program first opens a file named lseek.txt.  
 * It then uses _lseek to find the beginning of the file,  
 * to find the current position in the file, and to find  
 * the end of the file.  
 */  
  
#include <io.h>  
#include <fcntl.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
int main( void )  
{  
   int fh;  
   long pos;               /* Position of file pointer */  
   char buffer[10];  
  
   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );  
  
   /* Seek the beginning of the file: */  
   pos = _lseek( fh, 0L, SEEK_SET );  
   if( pos == -1L )  
      perror( "_lseek to beginning failed" );  
   else  
      printf( "Position for beginning of file seek = %ld\n", pos );  
  
   /* Move file pointer a little */  
    _read( fh, buffer, 10 );  
  
   /* Find current position: */  
   pos = _lseek( fh, 0L, SEEK_CUR );  
   if( pos == -1L )  
      perror( "_lseek to current position failed" );  
   else  
      printf( "Position for current position seek = %ld\n", pos );  
  
   /* Set the end of the file: */  
   pos = _lseek( fh, 0L, SEEK_END );  
   if( pos == -1L )  
      perror( "_lseek to end failed" );  
   else  
      printf( "Position for end of file seek = %ld\n", pos );  
  
   _close( fh );  
}  
```  
  
## 輸入:crt\_lseek.c\_input  
  
```  
Line one.  
Line two.  
Line three.  
Line four.  
Line five.  
```  
  
## Output  
  
```  
Position for beginning of file seek = 0  
Position for current position seek = 10  
Position for end of file seek = 57  
```  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [fseek、\_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_tell、\_telli64](../../c-runtime-library/reference/tell-telli64.md)