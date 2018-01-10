---
title: _ecvt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _ecvt
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
f1_keywords: _ecvt
dev_langs: C++
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 237924bce3bb4b659e72cec060738035d91c7cbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ecvt"></a>_ecvt
將 `double` 數字轉換為字串。 這個函式已有更安全的版本可用；請參閱 [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_ecvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 要轉換的數字。  
  
 `count`  
 儲存的位數。  
  
 `dec`  
 儲存的小數點位置。  
  
 `sign`  
 已轉換數字的正負號。  
  
## <a name="return-value"></a>傳回值  
 `_ecvt` 會傳回位數字串的指標；如果發生錯誤，則為 NULL。  
  
## <a name="remarks"></a>備註  
 `_ecvt` 函式會將浮點數轉換為字元字串。 `value` 參數是要轉換的浮點數。 此函式最多可將 `count` 位數的 `value` 儲存為字串，並在結尾處附加 null 字元 ('\0')。 如果 `value` 的位數超過 `count`，則會將低位數四捨五入。 如果少於 `count` 個位數，則以零填補字串。  
  
 `_ecvt` 傳回的總位數不會超過 `_CVTBUFSIZE`。  
  
 字串中只能儲存數字。 呼叫之後，可從 `dec` 和 `sign` 取得小數點位置和 `value` 的正負號。 `dec` 參數指向整數值，並提供字串開頭的小數點位置。 0 或負整數值表示小數點位於第一位數字的左邊。 `sign` 參數指向表示已轉換數字正負號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。  
  
 `_ecvt` 和 `_fcvt` 之間的差異位在 `count` 參數解譯中。 `_ecvt` 將 `count` 解譯為輸出字串的位數總數，而 `_fcvt` 將 `count` 解譯為小數點後的位數。  
  
 `_ecvt` 和 `_fcvt` 使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。  
  
 這個函式會驗證它的參數。 如果 `dec` 或 `sign` 為 NULL，或 `count` 為 0，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，且會傳回 NULL。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_ecvt`|\<stdlib.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0  
```  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)