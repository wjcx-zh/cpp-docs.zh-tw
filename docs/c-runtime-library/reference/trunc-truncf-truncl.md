---
title: "trunc、truncf、truncl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
dev_langs: C++
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 911636e4fa843afa1220dc99e1f679d5bfe88d7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="trunc-truncf-truncl"></a>trunc、truncf、truncl
判斷小於或等於指定浮點值且最接近的整數。  
  
## <a name="syntax"></a>語法  
  
```  
double trunc(  
   double x  
);  
  
float trunc(  
   float x  
); //C++ only  
  
long double trunc(  
   long double x  
); //C++ only  
  
float trunc(  
   float x  
); //C++ only  
  
long double truncl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `x`  
 要截斷的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 `x` 的整數值，並朝向零四捨五入。  
  
 否則，可能會傳回下列其中一項：  
  
|問題|Return|  
|-----------|------------|  
|`x`= ±INFINITY|x|  
|`x` =  ±0|x|  
|`x` = NAN|NaN|  
  
 依 [_matherr](../../c-runtime-library/reference/matherr.md) 中的指定回報錯誤。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和長雙精度浮點數類型的 `trunc` 多載。 在 C 程式中，`trunc` 一律採用及傳回雙精度浮點數。  
  
 因為浮點數的最大值是確切的整數，這個函式本身不會溢位。 不過，您可能會因為將值傳回到整數類型而造成函式溢位。  
  
 您也可以透過隱含地從浮點數轉換為整數進行無條件捨去。不過，這麼做受限於可以用目標類型儲存的值。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`trunc`,                `truncf`,  `truncl`|\<math.h>|\<cmath>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)