---
title: "長雙精度 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "10 位元組長雙精度"
  - "16 位元 Windows"
  - "32 位元 Windows"
  - "8 位元組長雙精度"
  - "80 位元精確度"
  - "80 位元精確度"
  - "8 位元組長雙精度"
  - "長雙精度"
ms.assetid: bb581e20-b5c2-4079-8ee8-ac6739a37852
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 長雙精度
Microsoft C\/C\+\+ 和 Microsoft Visual C\+\+ 先前支援 16 位元版本的 `long double`， 80 位元精確度資料型別。  在 Win32 程式設計中，不過， `long double` 資料型別對應至 `double`， 64 位精確度資料型別。  Microsoft 執行階段程式庫可以提供回溯相容性 \(Backward Compatibility\) 只提供數學函式的 `long double` 版本。  `long double` 函式原型與其 `double` 對應的原型相同，不同的是， `long` `double` 資料型別取代 `double` 資料型別。  這些函式 `long double` 版本不應該用於新的程式碼。  
  
### 雙重函式及其長雙對應項。  
  
|功能|Long double<br /><br /> 對應項。|功能|Long double<br /><br /> 對應項。|  
|--------|--------------------------|--------|--------------------------|  
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|`acosl`|[frexp](../c-runtime-library/reference/frexp.md)|`frexpl`|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|`asinl`|[\_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|`_hypotl`|  
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|`atanl`|[ldexp](../c-runtime-library/reference/ldexp.md)|`ldexpl`|  
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|`atan2l`|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|`logl`|  
|[atof](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|`_atold`|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|`log10l`|  
|[Bessel 函式： j0, j1, jn](../misc/bessel-functions-j0-j1-jn.md)|`j0l, j1l, jnl`|[\_matherr](../c-runtime-library/reference/matherr.md)|`_matherrl`|  
|[Bessel 函式： y0, y1, yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|`y0l, y1l, ynl`|[modf](../c-runtime-library/reference/modf-modff-modfl.md)|`modfl`|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|`_cabsl`|[pow](../c-runtime-library/reference/pow-powf-powl.md)|`powl`|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|`ceill`|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|`sinl`|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|`cosl`|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|`sinhl`|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|`coshl`|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|`sqrtl`|  
|[exp](../c-runtime-library/reference/exp-expf.md)|`expl`|[strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|`_strtold`|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|`fabsl`|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|`tanl`|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|`floorl`|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|`tanhl`|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|`fmodl`|||  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)