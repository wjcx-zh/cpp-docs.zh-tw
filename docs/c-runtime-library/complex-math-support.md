---
title: C 複雜數學支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.complex
dev_langs:
- C++
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3533d43783648c43b657c8073ada0c2042808b10
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2018
---
# <a name="c-complex-math-support"></a>C 複雜數學支援

Microsoft C 執行階段程式庫 (CRT) 提供複雜數學程式庫函式，包括 ISO C99 需要的所有項目。 編譯器並不會直接支援 **complex** 或 **_Complex** 關鍵字，因此 Microsoft 實作使用了結構類型來呈現複數。

實作這些函式可以平衡效能與正確性。 因為產生正確的四捨五入結果可能極為昂貴，所以這些函式會設計成有效率產生最接近正確四捨五入結果的近似值。 在大部分情況下，產生的結果是在正確四捨五入結果的 +/-1 ulp 內，但也可能出現較大的誤差。

複雜數學常式依賴浮點數學程式庫函式來進行實作。 這些函式對於不同的 CPU 架構有不同的實作。 例如，32 位元 x86 CRT 的實作可能和 64 位元 x64 CRT 的實作不同。 此外，某些函式對指定的 CPU 架構可能有多種實作。 在執行階段，會根據 CPU 支援的指令集動態選取最有效率的實作。 例如，在 32 位元 x86 CRT，有些函式同時有 x87 實作和 SSE2 實作。 在支援 SSE2 的 CPU 上執行時，會使用較快的 SSE2 實作。 在不支援 SSE2 的 CPU 上執行時，會使用較慢的 x87 實作。 因為數學程式庫函式的不同實作可能會使用不同的 CPU 指令和不同的演算法來產生結果，所以函式在不同的 CPU 中可能會產生不同的結果。 在大部分情況下，結果是在正確四捨五入結果的 +/-1 ulp 內，但實際的結果可能因 CPU 而異。

## <a name="types-used-in-complex-math"></a>在複雜數學中使用的類型

complex.h 標頭的 Microsoft 實作將這些類型定義為 C99 標準原生複雜類型的對等項：

|標準類型|Microsoft 類型|
|-|-|
|**float complex** 或 **float _Complex**|**_FComplex**|
|**double complex** 或 **double _Complex**|**_DComplex**|
|**long double complex** 或 **long double _Complex**|**_LComplex**|

math.h 標頭定義了個別類型 **struct _complex**，用於 [_cabs](../c-runtime-library/reference/cabs.md)函式。 **struct _complex** 類型不會受對等的複雜數學函式 [cabs、cabsf、cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)使用。

## <a name="complex-constants-and-macros"></a>複雜常數與巨集

**I** 定義為 `{ 0.0f, 1.0f }`所初始化的 **float** 複雜類型 **_FComplex**。

## <a name="trigonometric-functions"></a>三角函式

|功能|描述|
|-|-|
|[cacos、cacosf、cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|計算複數的弧形餘弦函數複數|
|[casin、casinf、casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|計算複數的弧形正弦函數複數|
|[catan、catanf、catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|計算複數的弧形正切函數複數|
|[ccos、ccosf、ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|計算複數的餘弦函數複數|
|[csin、csinf、csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|計算複數的正弦函數複數|
|[ctan、ctanf、ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|計算複數的正切函數複數|

## <a name="hyperbolic-functions"></a>雙曲線函式

|功能|描述|
|-|-|
|[cacosh、cacoshf、cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|計算複數的弧形雙曲餘弦函數複數|
|[casinh、casinhf、casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|計算複數的弧形雙曲正弦函數複數|
|[catanh、catanhf、catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|計算複數的弧形雙曲正切函數複數|
|[ccosh、ccoshf、ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|計算複數的雙曲餘弦函數複數|
|[csinh、csinhf、csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|計算複數的雙曲正弦函數複數|
|[ctanh、ctanhf、ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|計算複數的雙曲正切函數複數|

## <a name="exponential-and-logarithmic-functions"></a>指數和對數函數

|功能|描述|
|-|-|
|[cexp、cexpf、cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|計算複數之底數為 *e* 的指數複數|
|[clog、clogf、clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|計算複數的自然 (底數為 *e*) 對數複數|
|[clog10、clog10f、clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|計算複數之底數為 10 的對數複數|

## <a name="power-and-absolute-value-functions"></a>乘冪與絕對值函數

|功能|描述|
|-|-|
|[cabs、cabsf、cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|計算複數的絕對值複數 (又稱為範數、模數或大小)|
|[cpow、cpowf、cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|計算乘冪函數複數 x<sup>y</sup>|
|[csqrt、csqrtf、csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|計算複數的平方根複數|

## <a name="manipulation-functions"></a>操作函數

|功能|描述|
|-|-|
|[_Cbuild、_FCbuild、_LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|從實部及虛部建構複數|
|[carg、cargf、cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|計算複數的引數 (又稱相角)|
|[cimag、cimagf、cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|計算複數的虛部|
|[conj、conjf、conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|計算複數的共軛複數|
|[cproj、cprojf、cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|計算複數在黎曼球面上的投影|
|[creal、crealf、creall](../c-runtime-library/reference/creal-crealf-creall.md)|計算複數的實部|
|[norm、normf、norml](../c-runtime-library/reference/norm-normf-norml1.md)|計算複數的平方大小|

## <a name="operation-functions"></a>作業函數

因為複數並非 Microsoft 編譯器中的原生類型，所以並未在複雜類型上定義標準算數運算子。 為了方便起見，會提供這些複雜數學程式庫函數以在使用者程式碼中進行有限的複數操作：

|功能|描述|
|-|-|
|[_Cmulcc、_FCmulcc、_LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|將兩個複數相乘|
|[_Cmulcr、_FCmulcr、_LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|將複數與浮點數相乘|

## <a name="see-also"></a>另請參閱

[依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)