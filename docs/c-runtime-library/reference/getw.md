---
title: getw | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getw
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
- _getw
dev_langs:
- C++
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 96bf37d1cd8d04a47b1e7ae43252fcde369b5943
ms.lasthandoff: 02/24/2017

---
# <a name="getw"></a>_getw
從資料流中取得的整數。  
  
## <a name="syntax"></a>語法  
  
```  
int _getw(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 `_getw` 傳回讀取的整數值。 傳回值為 `EOF` 表示錯誤或檔案結尾。 不過，因為 `EOF` 值也是合法的整數值，所以請使用`feof` 或 `ferror` 來確認檔案結尾或錯誤狀況。 如果 `stream` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `EOF`。  
  
## <a name="remarks"></a>備註  
 `_getw` 函式會從與 `stream` 相關聯的檔案中讀取 `int` 類型的下一個二進位值，並遞增相關聯檔的案指標 (如果有的話)，以指向下一個未讀取的字元。 `_getw` 不會假設資料流中的項目有任何特殊對齊方式。 `_getw` 可能會發生移植的問題，因為 `int` 類型的大小和 `int` 類型內位元組順序於不同系統間有差異。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_getw`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_getw.c  
// This program uses _getw to read a word  
// from a stream, then performs an error check.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   FILE *stream;  
   int i;  
  
   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )  
      printf( "Couldn't open file\n" );  
   else  
   {  
      // Read a word from the stream:  
      i = _getw( stream );  
  
      // If there is an error...  
      if( ferror( stream ) )  
      {  
         printf( "_getw failed\n" );  
         clearerr_s( stream );  
      }  
      else  
         printf( "First data word in file: 0x%.4x\n", i );  
      fclose( stream );  
   }  
}  
```  
  
## <a name="input-crtgetwtxt"></a>輸入︰crt_getw.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>輸出  
  
```  
First data word in file: 0x656e694c  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_putw](../../c-runtime-library/reference/putw.md)
