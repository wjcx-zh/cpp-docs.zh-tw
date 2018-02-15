---
title: "ceil、ceilf、ceill | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcc33dd5fc9c00b537345d613cd47452a425a00e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ceil-ceilf-ceill"></a>ceil、ceilf、ceill
計算最大值。  
  
## <a name="syntax"></a>語法  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>參數  
 `x`  
 浮點值。  
  
## <a name="return-value"></a>傳回值  
 `ceil` 函式會傳回浮點值，代表大於或等於 `x` 的最小整數。 不會傳回錯誤。  
  
|輸入|SEH 例外狀況|Matherr 例外狀況|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|無|`_DOMAIN`|  
  
 `ceil` 有使用 Streaming SIMD Extensions 2 (SSE2) 的實作。 如需使用 SSE2 實作的資訊和限制，請參閱 [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md)。  
  
## <a name="remarks"></a>備註  
 因為 C++ 允許多載，所以您可以呼叫 `ceil` 的多載。 在 C 程式中，`ceil` 一律採用及傳回雙精度浮點數。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`ceil`, `ceilf`, `ceill`|\<math.h>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [floor](../../c-runtime-library/reference/floor-floorf-floorl.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod、fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)
