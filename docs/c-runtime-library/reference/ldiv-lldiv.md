---
title: "ldiv、lldiv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ldiv
- lldiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ldiv
- lldiv
dev_langs: C++
helpviewer_keywords:
- ldiv function
- lldiv function
- quotients, computing
- computing remainders
- remainder computing
- computing quotients
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c1da38d40c45ecd6dc36eed594304894a25dcc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ldiv-lldiv"></a>ldiv、lldiv
以一項作業計算商數和兩個整數的餘數。  
  
## <a name="syntax"></a>語法  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### <a name="parameters"></a>參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## <a name="return-value"></a>傳回值  
 `ldiv`傳回包含商數和餘數，類型為 [ldiv_t](../../c-runtime-library/standard-types.md) 的結構。 `lldiv` 傳回包含商數和餘數，類型為 [lldiv_t](../../c-runtime-library/standard-types.md) 的結構。  
  
## <a name="remarks"></a>備註  
 `ldiv` 和 `lldiv` 函式將 `numer` 除以 `denom`，並藉此計算商數及餘數。 商數的正負號與數學商數相同。 商數的絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會結束並出現錯誤訊息。 `ldiv` 和 `lldiv` 與 `div` 相同，除了 `ldiv` 的引數以及傳回的結構成員均為 `long` 類型，而`lldiv` 的引數和傳回結構的成員為 `long long` 類型。  
  
 `ldiv_t` 和 `lldiv_t` 在 \<stdlib.h> 中定義。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`ldiv`, `lldiv`|\<stdlib.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)