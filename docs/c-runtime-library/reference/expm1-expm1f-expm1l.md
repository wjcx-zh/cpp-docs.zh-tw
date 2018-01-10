---
title: "expm1、expm1f、expm1l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
dev_langs: C++
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8fe98cb7002bcdbf428115666e07401f26205733
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="expm1-expm1f-expm1l"></a>expm1、expm1f、expm1l
計算底數為 e 的指數值減一。  
  
## <a name="syntax"></a>語法  
  
```  
double expm1(   
   double x   
);  
float expm1(  
   float x  
);  // C++ only  
long double expm1(  
   long double x  
);  // C++ only  
float expm1f(  
   float x  
);  
long double expm1l(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 浮點指數值。  
  
## <a name="return-value"></a>傳回值  
 `expm1`函式會傳回浮點值，代表 e<sup>x</sup> -1，如果成功的話。 溢位時，`expm1` 傳回 `HUGE_VAL`、`expm1f` 傳回 `HUGE_VALF`、`expm1l` 傳回 `HUGE_VALL`，而 `errno` 設為 `ERANGE`。 如需傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回 `expm1` 和 `float` 值的 `long double` 的多載。 在 C 程式中，`expm1` 會一律採用並傳回 `double`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`expm1`, `expm1f`, `expm1l`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [exp2、exp2f、exp2l](http://msdn.microsoft.com/en-us/a7974629-be1e-4196-a562-6624a0732003)   
 [pow、powf、powl](../../c-runtime-library/reference/pow-powf-powl.md)