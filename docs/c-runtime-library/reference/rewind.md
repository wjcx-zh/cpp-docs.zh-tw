---
title: "rewind | Microsoft Docs"
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
  - "rewind"
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
  - "rewind"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "檔案指標 [C++]"
  - "檔案指標 [C++], 重新放置"
  - "重新放置檔案指標"
  - "rewind 函式"
ms.assetid: 1a460ce1-28d8-4b5e-83a6-633dca29c28a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rewind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新定位檔案指標至檔案的開頭。  
  
## 語法  
  
```  
  
      void rewind(  
   FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 指向 **FILE** 結構的指標。  
  
## 備註  
 **rewind** 函式變更位置檔案指標與 `stream` 相關聯之檔案的開頭。  對 **rewind** 的呼叫類似於  
  
 **\(void\) fseek\(** `stream`**, 0L,** `SEEK_SET` **\);**  
  
 不過，不同於 `fseek`， **rewind** 清除資料流的錯誤指示器以及檔案結尾指示器。  此外，不同於 `fseek`， **rewind** 不傳回值表示指標是否成功移動。  
  
 清除鍵盤緩衝區，搭配 `stdin` 使用 **rewind**，預設會與鍵盤相關聯。  
  
 如果資料流為 `NULL` 指標，較用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會返回且 `errno` 設為 `EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**rewind**|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_rewind.c  
/* This program first opens a file named  
 * crt_rewind.out for input and output and writes two  
 * integers to the file. Next, it uses rewind to  
 * reposition the file pointer to the beginning of  
 * the file and reads the data back in.  
 */  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int data1, data2;  
  
   data1 = 1;  
   data2 = -37;  
  
   fopen_s( &stream, "crt_rewind.out", "w+" );  
   if( stream != NULL )  
   {  
      fprintf( stream, "%d %d", data1, data2 );  
      printf( "The values written are: %d and %d\n", data1, data2 );  
      rewind( stream );  
      fscanf_s( stream, "%d %d", &data1, &data2 );  
      printf( "The values read are: %d and %d\n", data1, data2 );  
      fclose( stream );  
   }  
}  
```  
  
## Output  
  
```  
The values written are: 1 and -37  
The values read are: 1 and -37  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)