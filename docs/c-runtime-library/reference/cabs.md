---
title: _cabs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cabsl
- _cabs
- _cabsl
dev_langs:
- C++
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff48005643d5880e557dbbdcfc9f6f1c30fe68eb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cabs"></a>_cabs
計算複數的絕對值。  
  
## <a name="syntax"></a>語法  
  
```  
double _cabs(   
   struct _complex z   
);  
```  
  
#### <a name="parameters"></a>參數  
 `z`  
 複數。  
  
## <a name="return-value"></a>傳回值  
 成功時，`_cabs` 會傳回其引數的絕對值。 溢位時，`_cabs` 會傳回 `HUGE_VAL`，並將 `errno` 設為 `ERANGE`。 您可以使用 [_matherr](../../c-runtime-library/reference/matherr.md) 變更錯誤處理。  
  
## <a name="remarks"></a>備註  
 `_cabs` 函式會計算複數的絕對值，這必須是 [_complex](../../c-runtime-library/standard-types.md) 類型的結構。 結構 `z` 包含實數元件 `x` 和虛數元件 `y`。 呼叫`_cabs`產生同等的運算式值`sqrt( z.x * z.x + z.y * z.y )`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_cabs`|\<math.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
  
```  
// crt_cabs.c  
/* Using _cabs, this program calculates  
 * the absolute value of a complex number.  
 */  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct _complex number = { 3.0, 4.0 };  
   double d;  
  
   d = _cabs( number );  
   printf( "The absolute value of %f + %fi is %f\n",  
           number.x, number.y, d );  
}  
```  
  
```Output  
The absolute value of 3.000000 + 4.000000i is 5.000000  
```  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [abs、labs、llabs、_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [fabs、fabsf、fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   