---
title: _fcvt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fcvt
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
f1_keywords: _fcvt
dev_langs: C++
helpviewer_keywords:
- converting floating point, to strings
- _fcvt function
- floating-point functions, converting number to string
- fcvt function
- floating-point functions
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c66666d615dc94f74f17736de6011ec05f1eeca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fcvt"></a>_fcvt
將浮點數轉換為字串。 這個函式目前有更安全的版本，請參閱 [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_fcvt(   
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
 小數點後的小數位數。  
  
 `dec`  
 預存小數點位置的指標。  
  
 `sign`  
 預存正負號指標的指標。  
  
## <a name="return-value"></a>傳回值  
 `_fcvt` 會傳回位數字串的指標，發生錯誤的 NULL。  
  
## <a name="remarks"></a>備註  
 `_fcvt` 函式會將浮點數轉換成以 Null 結束的字元字串。 `value` 參數是要轉換的浮點數。 `_fcvt` 會將 `value` 的數字儲存為字串，並在結尾處附加 Null 字元 ('\0')。 `count` 參數會指定小數點後要儲存的位數。 多餘的數字會四捨五入至 `count` 位置。 如果有效位數少於 `count`，則以零填補字串。  
  
 `_fcvt` 傳回的總位數不會超過 `_CVTBUFSIZE`。  
  
 字串中只能儲存數字。 呼叫之後，可從 `dec` 和 sign 取得小數點位置和 `value` 的正負號。 `dec` 參數指向整數值，此整數值會提供字串開頭的小數點位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數 `sign` 指向表示 `value` 正負號的整數。 如果 `value` 是正值，則整數設定為 0；如果 `value` 是負值，則整數設定為非零的數字。  
  
 `_ecvt` 和 `_fcvt` 之間的差異位於 `count` 參數解譯中。 `_ecvt` 將 `count` 解譯為輸出字串的位數總數，而 `_fcvt` 將 `count` 解譯為小數點後的位數。  
  
 `_ecvt` 和 `_fcvt` 使用單一靜態配置的緩衝區來進行轉換。 每呼叫其中一個此等常式會導致先前呼叫結果的終結。  
  
 這個函式會驗證它的參數。 如果 `dec` 或 `sign` 為 NULL，或 `count` 為 0，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，且會傳回 NULL。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_fcvt`|\<stdlib.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
```Output  
source: 3.1415926535   buffer: '31415927'   decimal: 1   sign: 0  
```  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)