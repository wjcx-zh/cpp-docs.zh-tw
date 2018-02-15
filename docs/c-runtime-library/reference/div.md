---
title: div | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- div
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
- div
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2090ca5e08af74854177f02d6313d6c1304ed2c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="div"></a>div
計算兩個整數值的商數和餘數。  
  
## <a name="syntax"></a>語法  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### <a name="parameters"></a>參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## <a name="return-value"></a>傳回值  
 使用 `int` 類型的引數呼叫 `div` 會傳回 `div_t` 類型的結構，其中包括商數和餘數。 具有 `long` 類型引數之多載的傳回值為 `ldiv_t`。 `div_t` 和 `ldiv_t` 是在 STDLIB.H 中定義。  
  
## <a name="remarks"></a>備註  
 `div` 函式會將 `numer` 除以 `denom`，藉此計算商數和餘數。 [div_t](../../c-runtime-library/standard-types.md) 結構包含商數 `int quot` 和餘數 `int rem`。 商數的正負號與數學商數相同。 其絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會終止並出現錯誤訊息。  
  
 接受 `long` 或 `long long` 類型之引數的多載僅適用於 C++ 程式碼。 傳回型別 [ldiv_t](../../c-runtime-library/standard-types.md) 包含成員 `long quot` 和 `long rem`，而傳回型別 [lldiv_t](../../c-runtime-library/standard-types.md) 包含成員 `long long quot` 和 `long long rem`，其意義與 `div_t` 的成員相同。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`div`|\<stdlib.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
```Output  
x is 876, y is 13  
The quotient is 67, and the remainder is 5  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)