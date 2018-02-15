---
title: "ilogb、ilogbf、ilogbl2 | Microsoft Docs"
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
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8da5ba71b59f64c38a051fd8f31fa7bf58a4556d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb、ilogbf、ilogbl
擷取代表指定值之非偏誤基底 2 指數的整數。  
  
## <a name="syntax"></a>語法  
  
```  
int ilogb(  
   double x  
);  
  
int ilogb(  
   float x  
); //C++ only  
  
int ilogb(  
   long double x  
); //C++ only  
  
int ilogbf(  
   float x  
);  
  
int ilogbl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `x`  
 指定值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，以帶正負號的 `int` 值傳回`x` 的基底 2 指數。  
  
 否則會傳回如 \<math.h> 中定義的下列值：  
  
|輸入|結果|  
|-----------|------------|  
|±0|FP_ILOGB0|  
|±inf，±nan，無限|FP_ILOGBNAN|  
  
 依 [_matherr](../../c-runtime-library/reference/matherr.md) 中的指定回報錯誤。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫採用並傳回浮點和長雙精度浮點數類型的 `ilogb` 多載。 在 C 程式中，`ilogb` 一律採用及傳回雙精度浮點數。  
  
 呼叫此函式類似於呼叫對應的 `logb` 函式，然後將傳回值轉型成 `int`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|C 標頭|C++ 標頭|  
|-------------|--------------|------------------|  
|`ilogb`,                `ilogbf`,  `ilogbl`|\<math.h>|\<cmath>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [logb、logbf、logbl、_logb、_logbf](../../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)