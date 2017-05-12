---
title: "_fgetc_nolock、_fgetwc_nolock | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fgetc_nolock
- _fgetwc_nolock
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
- _fgetwc_nolock
- fgettc_nolock
- fgetwc_nolock
- _fgetc_nolock
- _fgettc_nolock
- fgetc_nolock
dev_langs:
- C++
helpviewer_keywords:
- fgetc_nolock function
- fgetwc_nolock function
- _fgetwc_nolock function
- characters, reading
- _fgetc_nolock function
- streams, reading characters from
- fgettc_nolock function
- reading characters from streams
- _fgettc_nolock function
ms.assetid: fb8e7c5b-4503-493a-879e-6a1db75aa114
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 9e22872f55161a78816c137ba3c4427c9efbd8cc
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="fgetcnolock-fgetwcnolock"></a>_fgetc_nolock、_fgetwc_nolock
從資料流讀取字元，不需要鎖定執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
int _fgetc_nolock(   
   FILE *stream   
);  
wint_t _fgetwc_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 請參閱 [fgetc、fgetwc](../../c-runtime-library/reference/fgetc-fgetwc.md)。  
  
## <a name="remarks"></a>備註  
 `_fgetc_nolock` 和 `_fgetwc_nolock` 分別與 `fgetc` 和 `fgetwc` 完全一致，不同之處在於其不受保護，不能免於其他執行緒的干擾。 因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_fgettc_nolock`|`_fgetc_nolock`|`_fgetc_nolock`|`_fgetwc_nolock`|  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`_fgetc_nolock`|\<stdio.h>|  
|`_fgetwc_nolock`|\<stdio.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_fgetc_nolock.c  
// This program uses getc to read the first  
// 80 input characters (or until the end of input)  
// and place them into a string named buffer.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   char buffer[81];  
   int  i, ch;  
  
   // Open file to read line from:   
   if( fopen_s( &stream, "crt_fgetc_nolock.txt", "r" ) != 0 )  
      exit( 0 );  
  
   // Read in first 80 characters and place them in "buffer":  
   ch = fgetc( stream );  
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )  
   {  
      buffer[i] = (char)ch;  
      ch = _fgetc_nolock( stream );  
   }  
  
   // Add null to end string   
   buffer[i] = '\0';  
   printf( "%s\n", buffer );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfgetcnolocktxt"></a>輸入︰crt_fgetc_nolock.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>輸出  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fputc、fputwc](../../c-runtime-library/reference/fputc-fputwc.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)
