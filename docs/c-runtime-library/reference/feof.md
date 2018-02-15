---
title: feof | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- feof
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feof
dev_langs:
- C++
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3946d03dd703bca93e399188ed6bfdc55017c76a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="feof"></a>feof
測試資料流的檔案結尾。  
  
## <a name="syntax"></a>語法  
  
```  
int feof(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 如果讀取作業已嘗試讀取超過檔案結尾，則 `feof` 函式會傳回非零值，否則會傳回 0。 如果資料流指標是 `NULL`，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且 `feof` 會傳回 0。  
  
 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `feof` 常式 (實作為函式和巨集) 會判斷是否已超過 `stream` 的結尾。 超過檔案結尾時，讀取作業會傳回檔案結尾指標直到資料流關閉，或者直到針對它呼叫 `rewind`、`fsetpos`、`fseek` 或 `clearerr`。  
  
 例如，如果檔案包含 10 個位元組，而您從檔案讀取 10 個位元組，`feof` 會傳回 0，因為即使檔案指標是在檔案結尾處，而您並未嘗試讀取超過結尾。 只有在您嘗試讀取第 11 個位元組之後，`feof` 才會傳回非零值。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`feof`|\<stdio.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_feof.c  
// This program uses feof to indicate when  
// it reaches the end of the file CRT_FEOF.TXT. It also  
// checks for errors with ferror.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int  count, total = 0;  
   char buffer[100];  
   FILE *stream;  
  
   fopen_s( &stream, "crt_feof.txt", "r" );  
   if( stream == NULL )  
      exit( 1 );  
  
   // Cycle until end of file reached:  
   while( !feof( stream ) )  
   {  
      // Attempt to read in 100 bytes:  
      count = fread( buffer, sizeof( char ), 100, stream );  
      if( ferror( stream ) )      {  
         perror( "Read error" );  
         break;  
      }  
  
      // Total up actual bytes read  
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfeoftxt"></a>輸入：crt_feof.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>輸出  
  
```  
Number of bytes read = 19  
```  
  
## <a name="see-also"></a>請參閱  
 [錯誤處理](../../c-runtime-library/error-handling-crt.md)   
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [_eof](../../c-runtime-library/reference/eof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror、_wperror](../../c-runtime-library/reference/perror-wperror.md)