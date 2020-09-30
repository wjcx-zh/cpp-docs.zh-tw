---
title: 泛型數學
description: 描述 <>tgmath.h> 中的宏>，可讓您更輕鬆地根據引數類型，撰寫呼叫正確數學函數的 C 程式碼。
ms.topic: conceptual
ms.date: 9/3/2020
helpviewer_keywords:
- CRT tgmath.h
ms.openlocfilehash: 98c786d91963973ad9384cea2fe6563d1e3174ac
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590221"
---
# <a name="type-generic-math"></a>泛型數學

針對 ISO C Standard 11 (C11) 和更新版本， \<tgmath.h> 除了包含和以外，標頭 \<math.h> 也 \<complex.h> 提供可根據參數類型叫用對應數學函數的宏。

C 執行時間程式庫數學函式是實作為複雜的變化。 根據引數的類型而定，每個變數都有三種類型： `float` 、 `double` 和 `long double` 。 因為 C c + + 不支援像 c + + 這樣的多載，所以每個變數的名稱都不同。 例如，若要取得實數浮點值的絕對值，您可以 `fabsf` `fabs` `fabsl` 根據您要 `float` 分別傳遞、 `double` 或 `long double` 值的方式，呼叫、或。 若要取得複雜的絕對值，您可以呼叫、或的其中一個 `cabsf` ， `cabs` `cabsl` 取決於您是否要 `float` 分別傳遞、 `double` 和 `long double` 複雜的值。 如果引數不符合上述任何一種類型，則會選擇函式，就像引數是雙精度浮點數一樣。

\<tgmath.h> 包含可簡化選取右邊數學函數的宏。 宏會檢查傳遞的型別，然後呼叫正確的函式。 例如， `sqrt` 宏會系結 `sqrt(9.9f)` 至 `sqrtf()` ，而會系結 `sqrt(9.9)` 至 `sqrt()` 。 如果泛型參數的至少一個宏引數很複雜，則宏會系結至複雜的函式;否則，它會叫用實際函數。

中的類型泛型宏可 \<tgmath.h> 讓您撰寫更多可移植的程式碼，因為您不需要管理轉換，或根據引數的類型來選取不同的函數名稱。

這些宏位於自己的標頭中，因此使用標頭撰寫的程式將 `<math.h>` 不會中斷。 因此， `double x = sin(42);` 當您包含時，其行為會一直存在 \<math.h> 。 儘管如此，在 \<tgmath.h> 包含標頭而非或時，大部分現有的 C 程式都不會受到影響 \<math.h> \<complex.h> 。

下表列出中可用的宏 \<tgmath.h> ，以及它們所擴充的功能。 `modf` 不包含在這個資料表中，因為它沒有對應的類型泛型宏，因為它不會清楚如何讓它保持安全，而不會讓型別解析更為複雜。

|巨集  |Real</br>`float`  | Real</br>`double` | Real</br>`long double` | Complex</br>`float` | Complex</br>`double` | Complex</br>`long double` |
|---------|---------|---------|---------|---------|---------|---------|
`acos` | [acosf](reference/mbsnbicmp-mbsnbicmp-l.md) | [acos](reference/mbsnbicmp-mbsnbicmp-l.md) | [acosl](reference/mbsnbicmp-mbsnbicmp-l.md) | [cacosf](reference/cacos-cacosf-cacosl.md) | [cacos](reference/cacos-cacosf-cacosl.md) | [cacosl](reference/cacos-cacosf-cacosl.md) |
`acosh` | [acoshf](reference/acosh-acoshf-acoshl.md) | [acosh](reference/acosh-acoshf-acoshl.md) | [acoshl](reference/acosh-acoshf-acoshl.md) | [cacoshf](reference/cacosh-cacoshf-cacoshl.md) | [cacosh](reference/cacosh-cacoshf-cacoshl.md) | [cacoshl](reference/cacosh-cacoshf-cacoshl.md) |
`asin` | [asinf](reference/asin-asinf-asinl.md) | [asin](reference/asin-asinf-asinl.md) | [asinl](reference/asin-asinf-asinl.md) | [casinf](reference/casin-casinf-casinl.md) | [casin](reference/casin-casinf-casinl.md) | [casinl](reference/casin-casinf-casinl.md) |
`asinh` | [asinhf](reference/asin-asinf-asinl.md) | [asinh](reference/asin-asinf-asinl.md) | [asinhl](reference/asin-asinf-asinl.md) | [casinhf](reference/casinh-casinhf-casinhl.md) | [casinh](reference/casinh-casinhf-casinhl.md) | [casinhl](reference/casinh-casinhf-casinhl.md) |
`atan` | [atanf](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atan](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atanl](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [catanf](reference/catan-catanf-catanl.md) | [catan](reference/catan-catanf-catanl.md) | [catanl](reference/catan-catanf-catanl.md) |
`atanh` | [atanhf](reference/atanh-atanhf-atanhl.md) | [atanh](reference/atanh-atanhf-atanhl.md) | [atanhl](reference/atanh-atanhf-atanhl.md) | [catanhf](reference/catanh-catanhf-catanhl.md) | [catanh](reference/catanh-catanhf-catanhl.md) | [catanhl](reference/catanh-catanhf-catanhl.md) |
`cos` | [cosf](reference/cos-cosf-cosl.md) | [因為](reference/cos-cosf-cosl.md) | [cosl](reference/cos-cosf-cosl.md) | [ccosf](reference/ccos-ccosf-ccosl.md) | [ccos](reference/ccos-ccosf-ccosl.md) | [ccosl](reference/ccos-ccosf-ccosl.md) |
`cosh` | [coshf](reference/cosh-coshf-coshl.md) | [cosh](reference/cosh-coshf-coshl.md) | [coshl](reference/cosh-coshf-coshl.md) | [ccoshf](reference/ccosh-ccoshf-ccoshl.md) | [ccosh](reference/ccosh-ccoshf-ccoshl.md) | [ccoshl](reference/ccosh-ccoshf-ccoshl.md) |
`exp` | [expf](reference/exp-expf.md) | [exp](reference/exp-expf.md) | [expl](reference/exp-expf.md) | [cexpf](reference/cexp-cexpf-cexpl.md) | [cexp](reference/cexp-cexpf-cexpl.md) | [cexpl](reference/cexp-cexpf-cexpl.md) |
`fabs` | [fabsf](reference/fabs-fabsf-fabsl.md) | [fabs](reference/fabs-fabsf-fabsl.md) | [fabsl](reference/fabs-fabsf-fabsl.md) | [cabsf](reference/cabs-cabsf-cabsl.md) | [計程車](reference/cabs-cabsf-cabsl.md) | [cabsl](reference/cabs-cabsf-cabsl.md) |
`log` | [logf](reference/log-logf-log10-log10f.md) | [日誌](reference/log-logf-log10-log10f.md) | [logl](reference/log-logf-log10-log10f.md) | [clogf](reference/clog-clogf-clogl.md) | [堵塞](reference/clog-clogf-clogl.md) | [clogl](reference/clog-clogf-clogl.md) |
`pow` | [powf](reference/pow-powf-powl.md) | [戰俘](reference/pow-powf-powl.md) | [powl](reference/pow-powf-powl.md) | [cpowf](reference/cpow-cpowf-cpowl.md) | [cpow](reference/cpow-cpowf-cpowl.md) | [cpowl](reference/cpow-cpowf-cpowl.md) |
`sin` | [sinf](reference/sin-sinf-sinl.md) | [罪](reference/sin-sinf-sinl.md) | [sinl](reference/sin-sinf-sinl.md) | [csinf](reference/csin-csinf-csinl.md) | [csin](reference/csin-csinf-csinl.md) | [csinl](reference/csin-csinf-csinl.md) |
`sinh` | [sinhf](reference/sinh-sinhf-sinhl.md) | [sinh](reference/sinh-sinhf-sinhl.md) | [sinhl](reference/sinh-sinhf-sinhl.md) | [csinhf](reference/csinh-csinhf-csinhl.md) | [csinh](reference/csinh-csinhf-csinhl.md) | [csinhl](reference/csinh-csinhf-csinhl.md) |
`sqrt` | [sqrtf](reference/sqrt-sqrtf-sqrtl.md) | [sqrt](reference/sqrt-sqrtf-sqrtl.md) | [sqrtl](reference/sqrt-sqrtf-sqrtl.md) | [csqrtf](reference/csqrt-csqrtf-csqrtl.md) | [csqrt](reference/csqrt-csqrtf-csqrtl.md) | [csqrtl](reference/csqrt-csqrtf-csqrtl.md) |
`tan` | [tanf](reference/tan-tanf-tanl.md) | [潭](reference/tan-tanf-tanl.md) | [tanl](reference/tan-tanf-tanl.md) | [ctanf](reference/ctan-ctanf-ctanl.md) | [ctan](reference/ctan-ctanf-ctanl.md) | [ctanl](reference/ctan-ctanf-ctanl.md) |
`tanh` | [tanhf](reference/tanh-tanhf-tanhl.md) | [tanh](reference/tanh-tanhf-tanhl.md) | [tanhl](reference/tanh-tanhf-tanhl.md) | [ctanhf](reference/ctanh-ctanhf-ctanhl.md) | [ctanh](reference/ctanh-ctanhf-ctanhl.md) | [ctanhl](reference/ctanh-ctanhf-ctanhl.md) |
`atan2` | [atan2f](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atan2](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | [atan2l](reference/atan-atanf-atanl-atan2-atan2f-atan2l.md) | - | - | - |
`cbrt` | [cbrtf](reference/cbrt-cbrtf-cbrtl.md) | [cbrt](reference/cbrt-cbrtf-cbrtl.md) | [cbrtl](reference/cbrt-cbrtf-cbrtl.md) | - | - | - |
`ceil` | [ceilf](reference/ceil-ceilf-ceill.md) | [ceil](reference/ceil-ceilf-ceill.md) | [ceill](reference/ceil-ceilf-ceill.md) | - | - | - |
`copysign` | [copysignf](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [copysign](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | [copysignl](reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md) | - | - | - |
`erf` | [erff](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erf](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erfl](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`erfc` | [erfcf](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erfc](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | [erfcl](reference/erf-erff-erfl-erfc-erfcf-erfcl.md) | - | - | - |
`exp2` | [exp2f](reference/exp2-exp2f-exp2l.md) | [exp2](reference/exp2-exp2f-exp2l.md) | [exp2l](reference/exp2-exp2f-exp2l.md) | - | - | - |
`expm1` | [expm1f](reference/expm1-expm1f-expm1l.md) | [expm1](reference/expm1-expm1f-expm1l.md) | [expm1l](reference/expm1-expm1f-expm1l.md) | - | - | - |
`fdim` | [fdimf](reference/fdim-fdimf-fdiml.md) | [fdim](reference/fdim-fdimf-fdiml.md) | [fdiml](reference/fdim-fdimf-fdiml.md) | - | - | - |
`floor` | [floorf](reference/floor-floorf-floorl.md) | [地板](reference/floor-floorf-floorl.md) | [floorl](reference/floor-floorf-floorl.md) | - | - | - |
`fma` | [fmaf](reference/fma-fmaf-fmal.md) | [fma](reference/fma-fmaf-fmal.md) | [fmal](reference/fma-fmaf-fmal.md) | - | - | - |
`fmax` | [fmaxf](reference/fmax-fmaxf-fmaxl.md) | [fmax](reference/fmax-fmaxf-fmaxl.md) | [fmaxl](reference/fmax-fmaxf-fmaxl.md) | - | - | - |
`fmin` | [fminf](reference/fmin-fminf-fminl.md) | [fmin](reference/fmin-fminf-fminl.md) | [fminl](reference/fmin-fminf-fminl.md) | - | - | - |
`fmod` | [fmodf](reference/fmod-fmodf.md) | [fmod](reference/fmod-fmodf.md) | [fmodl](reference/fmod-fmodf.md) | - | - | - |
`frexp` | [frexpf](reference/frexp.md) | [frexp](reference/frexp.md) | [frexpl](reference/frexp.md) | - | - | - |
`hypot` | [hypotf](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [hypot](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | [hypotl](reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md) | - | - | - |
`ilogb` | [ilogbf](reference/ilogb-ilogbf-ilogbl2.md) | [ilogb](reference/ilogb-ilogbf-ilogbl2.md) | [ilogbl](reference/ilogb-ilogbf-ilogbl2.md) | - | - | - |
`ldexp` | [ldexpf](reference/ldexp.md) | [ldexp](reference/ldexp.md) | [ldexpl](reference/ldexp.md) | - | - | - |
`lgamma` | [lgammaf](reference/lgamma-lgammaf-lgammal.md) | [lgamma](reference/lgamma-lgammaf-lgammal.md) | [lgammal](reference/lgamma-lgammaf-lgammal.md) | - | - | - |
`llrint` | [llrintf](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [llrint](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [llrintl](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`llround` | [llroundf](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [llround](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [llroundl](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`log10` | [log10f](reference/log-logf-log10-log10f.md) | [log10](reference/log-logf-log10-log10f.md) | [log10l](reference/log-logf-log10-log10f.md) | - | - | - |
`log1p` | [log1pf](reference/log1p-log1pf-log1pl2.md) | [log1p](reference/log1p-log1pf-log1pl2.md) | [log1pl](reference/log1p-log1pf-log1pl2.md) | - | - | - |
`log2` | [log2f](reference/log2-log2f-log2l.md) | [log2](reference/log2-log2f-log2l.md) | [log2l](reference/log2-log2f-log2l.md) | - | - | - |
`logb` | [logbf](reference/logb-logbf-logbl-logb-logbf.md) | [logb](reference/logb-logbf-logbl-logb-logbf.md) | [logbl](reference/logb-logbf-logbl-logb-logbf.md) | - | - | - |
`lrint` | [lrintf](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [lrint](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | [lrintl](reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md) | - | - | - |
`lround` | [lroundf](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [lround](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | [lroundl](reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md) | - | - | - |
`nearbyint` | [nearbyintf](reference/nearbyint-nearbyintf-nearbyintl1.md) | [nearbyint](reference/nearbyint-nearbyintf-nearbyintl1.md) | [nearbyintl](reference/nearbyint-nearbyintf-nearbyintl1.md) | - | - | - |
`nextafter` | [nextafterf](reference/nextafter-functions.md) | [nextafter](reference/nextafter-functions.md) | [nextafterl](reference/nextafter-functions.md) | - | - | - |
`nexttoward` | [nexttowardf](reference/nextafter-functions.md) | [nexttoward](reference/nextafter-functions.md) | [nexttowardl](reference/nextafter-functions.md) | - | - | - |
`remainder` | [remainderf](reference/remainder-remainderf-remainderl.md) | [剩餘](reference/remainder-remainderf-remainderl.md) | [remainderl](reference/remainder-remainderf-remainderl.md) | - | - | - |
`remquo` | [remquof](reference/remquo-remquof-remquol.md) | [remquo](reference/remquo-remquof-remquol.md) | [remquol](reference/remquo-remquof-remquol.md) | - | - | - |
`rint` | [rintf](reference/rint-rintf-rintl.md) | [rint](reference/rint-rintf-rintl.md) | [rintl](reference/rint-rintf-rintl.md) | - | - | - |
`round` | [roundf](reference/round-roundf-roundl.md) | [輪](reference/round-roundf-roundl.md) | [roundl](reference/round-roundf-roundl.md) | - | - | - |
`scalbln` | [scalblnf](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalbln](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalblnl](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`scalbn` | [scalbnf](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalbn](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | [scalbnl](reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md) | - | - | - |
`tgamma` | [tgammaf](reference/tgamma-tgammaf-tgammal.md) | [tgamma](reference/tgamma-tgammaf-tgammal.md) | [tgammal](reference/tgamma-tgammaf-tgammal.md) | - | - | - |
`trunc` | [truncf](reference/trunc-truncf-truncl.md) | [trunc](reference/trunc-truncf-truncl.md) | [truncl](reference/trunc-truncf-truncl.md) | - | - | - |
`carg` | - | - | - | [cargf](reference/carg-cargf-cargl.md) | [carg](reference/carg-cargf-cargl.md) | [cargl](reference/carg-cargf-cargl.md) |
`conj` | - | - | - | [conjf](reference/conj-conjf-conjl.md) | [conj](reference/conj-conjf-conjl.md) | [conjl](reference/conj-conjf-conjl.md) |
`creal` | - | - | - | [crealf](reference/creal-crealf-creall.md) | [creal](reference/creal-crealf-creall.md) | [creall](reference/creal-crealf-creall.md) |
`cimag` | - | - | - | [cimagf](reference/cimag-cimagf-cimagl.md) | [cimag](reference/cimag-cimagf-cimagl.md) | [cimagl](reference/cimag-cimagf-cimagl.md) |
`cproj` | - | - | - | [cprojf](reference/cproj-cprojf-cprojl.md) | [cproj](reference/cproj-cprojf-cprojl.md) | [cprojl](reference/cproj-cprojf-cprojl.md) |

## <a name="requirements"></a>需求

[std：需要 c + + 11](../build/reference/std-specify-language-standard-version.md) 或更新版本。

Windows SDK 版本10.0.20201.0 或更新版本。

## <a name="see-also"></a>另請參閱

[C 執行時間程式庫參考](c-run-time-library-reference.md)
