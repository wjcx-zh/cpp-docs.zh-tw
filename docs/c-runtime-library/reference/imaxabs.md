---
title: imaxabs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- imaxabs
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
- imaxabs
dev_langs:
- C++
helpviewer_keywords:
- imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
caps.latest.revision: 7
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
ms.sourcegitcommit: 467f967446b0dd4976fa0fc695924a97b471a6b6
ms.openlocfilehash: 1e721b0c0900ae476bbe4c531f265369d004ab37
ms.lasthandoff: 02/24/2017

---
# <a name="imaxabs"></a>imaxabs
計算任何大小之整數的絕對值。  
  
## <a name="syntax"></a>語法  
  
```  
intmax_t imaxabs(  
   intmax_t n   
);  
```  
  
#### <a name="parameters"></a>參數  
 *n*  
 整數值。  
  
## <a name="return-value"></a>傳回值  
 `imaxabs` 函式會傳回引數的絕對值。 不會傳回錯誤。  
  
> [!NOTE]
>  因為可以使用 `intmax_t` 的負數整數範圍大於可代表的正整數範圍，您可以提供無法轉換的引數至 `imaxabs`。 如果引數的絕對值無法以傳回類型代表，則 `imaxabs` 未定義。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`imaxabs`|\<inttypes.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_imaxabs.c  
// Build using: cl /W3 /Tc crt_imaxabs.c  
// This example calls imaxabs to compute an  
// absolute value, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x = LLONG_MIN + 2;  
  
   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));  
}  
```  
  
```Output  
The absolute value of -9223372036854775806 is 9223372036854775806  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [abs、labs、llabs、_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
