---
title: 數學與浮點支援
description: '描述 Microsoft 通用 C 執行時間程式庫中的浮點支援 (UCRT) '
ms.date: 9/14/2020
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: d1caaf5c9c0cfc7a3b6650bcb72a66b4c0028e28
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502118"
---
# <a name="math-and-floating-point-support"></a>數學與浮點支援

通用 C 執行階段程式庫 (UCRT) 提供許多整數和浮點數學程式庫函式，包括 ISO C99 需要的所有項目。 實作這些浮點函式可以平衡效能與正確性。 因為產生正確的四捨五入結果可能極為昂貴，所以這些函式會設計成有效率產生最接近正確四捨五入結果的近似值。 在大部分情況下，產生的結果是在正確四捨五入結果的 +/-1 ulp 內，但也可能出現較大的誤差。

針對 ISO C Standard 11 (C11) 和更新版本， \<tgmath.h> 除了包含和以外，標頭 \<math.h> 也 \<complex.h> 提供可根據參數類型叫用對應數學函數的宏。 如需詳細資料，請參閱 [類型-泛型數學](tgmath.md) 。

許多浮點數學程式庫函式對不同的 CPU 架構會有不同的實作。 例如，32 位元 x86 CRT 的實作可能和 64 位元 x64 CRT 的實作不同。 此外，某些函式對指定的 CPU 架構可能有多種實作。 在執行階段，會根據 CPU 支援的指令集動態選取最有效率的實作。 例如，在 32 位元 x86 CRT，有些函式同時有 x87 實作和 SSE2 實作。 在支援 SSE2 的 CPU 上執行時，會使用較快的 SSE2 實作。 在不支援 SSE2 的 CPU 上執行時，會使用較慢的 x87 實作。 因為數學程式庫函式的不同實作可能會使用不同的 CPU 指令和不同的演算法來產生結果，所以函式在不同的 CPU 中可能會產生不同的結果。 在大部分情況下，結果是在正確四捨五入結果的 +/-1 ulp 內，但實際的結果可能因 CPU 而異。

先前的16位版本的 Microsoft C/c + + 和 Microsoft Visual C++ 支援 **`long double`** 以80位精確度浮點數資料類型做為類型。 在 Visual C++ 的較新版本中， **`long double`** 資料類型是與類型相同的64位有效位數浮點數資料類型 **`double`** 。 編譯器會將 **`long double`** 和視為 **`double`** 相異類型，但函式 **`long double`** 與其對應專案相同 **`double`** 。 CRT 提供 **`long double`** ISO C99 原始程式碼相容性的數學函式版本，但請注意，二進位標記法可能與其他編譯器不同。

## <a name="supported-math-and-floating-point-routines"></a>支援的數學與浮點常式

|常式傳回的值|使用|
|-|-|
[abs、labs、llabs、_abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|計算任何類型整數的絕對值
[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|計算反餘弦值
[acosh、acoshf、acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|計算雙曲反餘弦值
[asin、asinf、asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|計算反正弦值
[asinh、asinhf、asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|計算雙曲反正弦值
[atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|計算反正切值
[atanh、atanhf、atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|計算雙曲反正切值
[_atodbl、_atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|將地區設定特定字串轉換成 **`double`**
[atof、_atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將字串轉換為 **`double`**
[_atoflt、_atoflt_l、_atoldbl、_atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|將地區設定特定字串轉換成 **`float`** 或 **`long double`**
[cbrt、cbrtf、cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|計算立方根
[ceil、ceilf、ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|計算 ceiling
[_chgsign、_chgsignf、_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|計算加法反元素
[_clear87、_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|取得及清除浮點狀態暫存器
[_control87、\__control87_2、_controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|取得和設定浮點控制字組
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|更安全的 **_controlfp** 版本
[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|傳回一個值，具有其中一個引數的大小和另一個引數的正負號
[cos、cosf、cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|計算正弦值
[cosh、coshf、coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|計算雙曲正弦值
[div、ldiv、lldiv](../c-runtime-library/reference/div.md)|計算兩個整數值的商數和餘數
[_ecvt](../c-runtime-library/reference/ecvt.md)、[ecvt](../c-runtime-library/reference/posix-ecvt.md)|將轉換 **`double`** 成字串
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|更安全的 **_ecvt** 版本
[erf、erff、erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|計算誤差函式
[erfc、erfcf、erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|計算誤差餘函式
[exp、expf、expl](../c-runtime-library/reference/exp-expf.md)|計算指數 *e*<sup>x</sup>
[exp2、exp2f、exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|計算指數 2<sup>x</sup>
[expm1、expm1f、expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|計算 *e*<sup>x</sup>-1
[fabs、fabsf、fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|計算浮點類型的絕對值
[_fcvt](../c-runtime-library/reference/fcvt.md)、[fcvt](../c-runtime-library/reference/posix-fcvt.md)|將浮點數轉換為字串
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|更安全的 **_fcvt** 版本
[fdim、fdimf、fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|判斷兩值之間的正差
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|清除指定的浮點例外狀況
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|儲存目前的浮點環境
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|取得指定的浮點例外狀況狀態
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|取得浮點進位模式
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|設定持續的浮點例外狀況模式
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|引發指定的浮點例外狀況
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|設定目前的浮點環境
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|設定指定的浮點狀態旗標
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|設定指定的浮點進位模式
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|決定要設定的浮點例外狀況狀態旗標
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|先還原浮點環境再引發前一個例外狀況
[floor、floorf、floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|計算 floor
[fma、fmaf、fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|計算積和熔加
[fmax、fmaxf、fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|計算引數的上限
[fmin、fminf、fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|計算引數的最小值
[fmod、fmodf、fmodl](../c-runtime-library/reference/fmod-fmodf.md)|計算浮點餘數
[_fpclass、_fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|傳回浮點值的分類
[fpclassify](../c-runtime-library/reference/fpclassify.md)|傳回浮點值的分類
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|設定浮點例外狀況的處理常式
[_fpreset](../c-runtime-library/reference/fpreset.md)|重設浮點環境
[frexp、frexpf、frexpl](../c-runtime-library/reference/frexp.md)|取得浮點數的尾數和指數
[_gcvt](../c-runtime-library/reference/gcvt.md)、[gcvt](../c-runtime-library/reference/posix-gcvt.md)|將浮點數轉換為字串
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|更安全的 **_gcvt** 版本
[_get_FMA3_enable、_set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|取得或設定在 x64 上使用 FMA3 指令的旗標
[hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|計算斜邊
[ilogb、ilogbf、ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|計算以 2 為底數的整數指數
[imaxabs](../c-runtime-library/reference/imaxabs.md)|計算任何類型整數的絕對值
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|計算兩個整數值的商數和餘數
[isfinite、_finite、_finitef](../c-runtime-library/reference/finite-finitef.md)|判斷值是否有限
[isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered](../c-runtime-library/reference/floating-point-ordering.md)|比較兩個浮點值的順序
[isinf](../c-runtime-library/reference/isinf.md)|判斷指定的浮點值是否無限
[isnan、_isnan、_isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|測試 NaN 的浮點值
[isnormal](../c-runtime-library/reference/isnormal.md)|測試浮點值是否為有限且為次正規數
[_j0、_j1 _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|計算 Bessel 函式
[ldexp、ldexpf、ldexpl](../c-runtime-library/reference/ldexp.md)|計算 x*2<sup>n</sup>
[lgamma、lgammaf、lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|計算 gamma 函式絕對值的自然對數
[llrint、llrintf、llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|將浮點值四捨五入為最接近的 **`long long`** 值
[llround、llroundf、llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|將浮點值四捨五入為最接近的 **`long long`** 值
[log、logf、logl、log10、log10f、log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|計算自然對數或底數為 10 的對數
[log1p、log1pf、log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|計算 1+x 的自然對數
[log2、log2f、log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|計算以 2 為底數的對數
[logb、logbf、logbl、_logb、_logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|傳回浮點值的指數
[lrint、lrintf、lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|將浮點值四捨五入為最接近的 **`long`** 值
[_lrotl、_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|將整數值向左或向右旋轉
[lround、lroundf、lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|將浮點值四捨五入為最接近的 **`long`** 值
[_matherr](../c-runtime-library/reference/matherr.md)|預設數學錯誤處理常式
[__max](../c-runtime-library/reference/max.md)|傳回兩個值中較大值的巨集
[__min](../c-runtime-library/reference/min.md)|傳回兩個值中較小值的巨集
[modf、modff、modfl](../c-runtime-library/reference/modf-modff-modfl.md)|將浮點值分割成小數和整數部分
[nan、nanf、nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|傳回無訊息 NaN 值
[nearbyint、nearbyintf、nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|傳回進位的值
[nextafter、nextafterf、nextafterl、_nextafter、_nextafterf](../c-runtime-library/reference/nextafter-functions.md)|傳回下一個所能顯示的浮點值
[nexttoward、nexttowardf、nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|傳回下一個所能顯示的浮點值
[pow、powf、powl](../c-runtime-library/reference/pow-powf-powl.md)|傳回 *x*<sup>*y*</sup> 的值
[remainder、remainderf、remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|計算兩個浮點值商數的餘數
[remquo、remquof、remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|計算兩個整數值的餘數
[rint、rintf、rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|進位浮點值
[_rotl、_rotl64、_rotr、_rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|旋轉整數類型的位元
[round、roundf、roundl](../c-runtime-library/reference/round-roundf-roundl.md)|進位浮點值
[_scalb、_scalbf](../c-runtime-library/reference/scalb.md)|將引數依 2 的乘冪進位
[scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|將浮點數與 **FLT_RADIX** 的整數冪相乘
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|設定浮點控制字組
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|啟用或停用 SSE2 指令
[signbit](../c-runtime-library/reference/signbit.md)|測試浮點值的正負號位元
[sin、sinf、sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|計算正弦值
[sinh、sinhf、sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|計算雙曲正弦值
[sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|計算平方根
[_status87、_statusfp、_statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|取得浮點狀態字組
[strtof、_strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|將字串轉換為 **`float`**
[strtold、_strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|將字串轉換為 **`long double`**
[tan、tanf、tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|計算正切值
[tanh、tanhf、tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|計算雙曲正切值
[tgamma、tgammaf、tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|計算 gamma 函式
[trunc、truncf、truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|截斷小數部分
[_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|將寬字元串轉換為 **`double`**
[_y0、_y1 _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|計算 Bessel 函式

## <a name="see-also"></a>另請參閱

[依類別分類的通用 C 執行時間常式](../c-runtime-library/run-time-routines-by-category.md)\
[浮點數基本類型](../c-runtime-library/reference/floating-point-primitives.md)
