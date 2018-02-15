---
title: "log1p、log1pf、log1pl2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f99c09efd055cc60162e88e52e938df690929a1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="log1p-log1pf-log1pl"></a>log1p、log1pf、log1pl
計算 1 加上指定值的自然對數。  
  
## <a name="syntax"></a>語法  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 浮點引數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 (`x`+1) 的自然 (以 e 為底數) 對數。  
  
 否則，可能會傳回下列其中一個值：  
  
|輸入|結果|SEH 例外狀況|errno|  
|-----------|------------|-------------------|-----------|  
|+inf|+inf|||  
|非正規數|與輸入相同|UNDERFLOW||  
|±0|與輸入相同|||  
|-1|-inf|DIVBYZERO|ERANGE|  
|< -1|NAN|INVALID|EDOM|  
|-inf|NAN|INVALID|EDOM|  
|±SNaN|與輸入相同|INVALID||  
|無限期 ±QNaN|與輸入相同|||  
  
 如果 `x` = -1，`errno` 值會設定為 ERANGE。 `errno`如果值設定為 EDOM `x` <-1。  
  
## <a name="remarks"></a>備註  
 當 x 趨近於 0 時，`log1p` 函式可能比使用 log(`x`+1) 更準確。  
  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和 long double 類型的 `log1p` 多載。 在 C 程式中，`log1p` 會一律採用並傳回雙精度浮點數。  
  
 如果 `x` 為自然數，此函式會傳回 (`x`-1) 階乘的對數。  
  
## <a name="requirements"></a>需求  
  
|功能|C 標頭|C++ 標頭|  
|--------------|--------------|------------------|  
|`log1p`,                `log1pf`,  `log1pl`|\<math.h>|\<cmath>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2、log2f、log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log、logf、log10、log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)