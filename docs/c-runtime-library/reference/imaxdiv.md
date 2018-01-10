---
title: imaxdiv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: imaxdiv
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
f1_keywords: imaxdiv
dev_langs: C++
helpviewer_keywords: imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7a6dbcd5b25fe1a8b1b21b2e2f6ac7a8cc99cc06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="imaxdiv"></a>imaxdiv
以單一作業計算任何大小之兩個整數值的商數和餘數。  
  
## <a name="syntax"></a>語法  
  
```  
imaxdiv_t imaxdiv(   
   intmax_t numer,  
   intmax_t denom   
);   
```  
  
#### <a name="parameters"></a>參數  
 `numer`  
 分子。  
  
 `denom`  
 分母。  
  
## <a name="return-value"></a>傳回值  
 以 [intmax_t](../../c-runtime-library/standard-types.md) 類型的引數呼叫的 `imaxdiv` 會傳回由商數和餘數組成的 [imaxdiv_t](../../c-runtime-library/standard-types.md) 類型結構。  
  
## <a name="remarks"></a>備註  
 `imaxdiv` 函式會將 `numer` 除以 `denom`，藉此計算商數和餘數。 `imaxdiv_t` 結構包含商數 `intmax_t quot` 和餘數 `intmax_t rem`。 商數的正負號與數學商數相同。 其絕對值是小於數學商數絕對值的最大整數。 如果分母為 0，程式會終止並出現錯誤訊息。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`imaxdiv`|\<inttypes.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_imaxdiv.c  
// Build using: cl /W3 /Tc crt_imaxdiv.c  
// This example takes two integers as command-line  
// arguments and calls imaxdiv to divide the first   
// argument by the second, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x,y;  
   imaxdiv_t div_result;  
  
   x = atoll(argv[1]);  
   y = atoll(argv[2]);  
  
   printf("The call to imaxdiv(%lld, %lld)\n", x, y);  
   div_result = imaxdiv(x, y);  
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",  
          div_result.quot, div_result.rem);  
}  
```  
  
 建置後以命令列參數 `9460730470000000 8766` 呼叫，程式碼會產生以下輸出︰  
  
```Output  
The call to imaxdiv(9460730470000000, 8766)  
results in a quotient of 1079252848505, and a remainder of 5170  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [ldiv、lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)