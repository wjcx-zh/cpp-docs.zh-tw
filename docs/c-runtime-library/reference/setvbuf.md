---
title: setvbuf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: setvbuf
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
f1_keywords: setvbuf
dev_langs: C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5020a0186399ec35fb42a0479f7466318c45c18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="setvbuf"></a>setvbuf
控制資料流緩衝處理和緩衝區大小。  
  
## <a name="syntax"></a>語法  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
 `buffer`  
 使用者配置的緩衝區。  
  
 `mode`  
 緩衝處理的模式。  
  
 `size`  
 緩衝區大小 (以位元組為單位)。 允許的範圍︰2 <= `size` <= INT_MAX (2147483647)。 就內部而言，針對 `size` 提供的值會向下捨入為最近的 2 倍數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 0。  
  
 如果 `stream` 為 `NULL`，或者 `mode` 或 `size` 不在有效變更內，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
 如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `setvbuf` 函式可讓程式控制 `stream` 的緩衝處理和緩衝區大小。 `stream` 必須參考因已開啟而未進行 I/O 作業的開啟檔案。 除非 `buffer` 為 `NULL`，否則會將其所指向的陣列用作緩衝區，在此情況下，`setvbuf` 會使用長度為 `size`/2 * 2 位元組的自動配置緩衝區。  
  
 模式必須是 `_IOFBF`、`_IOLBF` 或 `_IONBF`。 如果 `mode` 為 `_IOFBF` 或 `_IOLBF`，則會將 `size` 用作緩衝區的大小。 如果 `mode` 為 `_IONBF`，則不會緩衝處理資料流，並忽略 `size` 和 `buffer`。 `mode` 的值和其意義如下：  
  
 `_IOFBF`  
 完整緩衝處理；亦即，將 `buffer` 用作緩衝區，並將 `size` 用作緩衝區的大小。 如果 `buffer` 為 `NULL`，則會使用自動配置的緩衝區 `size` 位元組長度。  
  
 `_IOLBF`  
 對於某些系統，這提供行緩衝處理。 不過，對於 Win32，行為與 `_IOFBF` 相同 - 完整緩衝處理。  
  
 `_IONBF`  
 不論 `buffer` 或 `size`，都不會使用緩衝區。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`setvbuf`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
```Output  
'stream1' now has a buffer of 1024 bytes  
'stream2' now has no buffer  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)