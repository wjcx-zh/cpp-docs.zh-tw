---
title: _gcvt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _gcvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _gcvt
dev_langs:
- C++
helpviewer_keywords:
- _gcvt function
- _CVTBUFSIZE
- gcvt function
- floating-point functions, converting number to string
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
caps.latest.revision: 25
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
ms.openlocfilehash: 055d1e6d996a076ca7f1a49e21abf3771fa543fb
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="gcvt"></a>_gcvt
將浮點值轉換為字串，接著儲存在緩衝區中。 目前有比這個函式更安全的版本可供使用；請參閱 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_gcvt(   
   double value,  
   int digits,  
   char *buffer   
);  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 要轉換的值。  
  
 `digits`  
 儲存的重要數字的數目。  
  
 `buffer`  
 結果的儲存位置。  
  
## <a name="return-value"></a>傳回值  
 `_gcvt` 傳回指標至數字字串。  
  
## <a name="remarks"></a>備註  
 `_gcvt` 函式會將浮點 `value` 轉換為字元字串 (其中包括小數點和可能的正負號位元組)，並將字串儲存在 `buffer` 中。 `buffer` 應該大到足以容納轉換的值加上會自動予以附加的結束 Null 字元。 如果使用的緩衝區大小為 `digits` + 1 ，則函式會覆寫緩衝區結尾。 這是因為已轉換的字串包含小數點，且可以包含符號和指數的資訊。 沒有提供溢位。 `_gcvt` 嘗試以十進位格式產生 `digits` 個數字。 如果不行，它會以指數格式產生 `digits` 個數字。 可能於轉換中隱藏尾端零。  
  
 長度為`_CVTBUFSIZE`的`buffer`足可供任何浮點值使用。  
  
 這個函式會驗證它的參數。 如果`buffer`為`NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `NULL`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_gcvt`|\<stdlib.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_gcvt.c  
// compile with: /W3  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   char buffer[_CVTBUFSIZE];  
   double value = -1234567890.123;  
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );  
   _gcvt( value, 12, buffer ); // C4996  
   // Note: _gcvt is deprecated; consider using _gcvt_s instead  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
  
   printf( "\n" );  
   value = -12.34567890123;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
}  
```  
  
```Output  
The following numbers were converted by _gcvt(value,12,buffer):  
buffer: '-1234567890.12' (14 chars)  
buffer: '-12345678901.2' (14 chars)  
buffer: '-123456789012' (13 chars)  
buffer: '-1.23456789012e+012' (19 chars)  
  
buffer: '-12.3456789012' (14 chars)  
buffer: '-1.23456789012' (14 chars)  
buffer: '-0.123456789012' (15 chars)  
buffer: '-1.23456789012e-002' (19 chars)  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)
