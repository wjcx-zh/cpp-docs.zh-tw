---
title: /fp (指定浮點數行為)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: f85f9b397ef3ab5bd070be1f4c81845405b14020
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234376"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (指定浮點數行為)

指定編譯器如何對待浮點運算式、優化和例外狀況。 **/Fp**選項會指定產生的程式碼是否允許浮點環境變更為進位模式、例外狀況遮罩和偏低行為，以及浮點狀態檢查是否傳回目前的精確結果。 它會控制編譯器是否會產生程式碼來維護來源作業和運算式順序，並遵循 NaN 傳播的標準，或者，如果它改為產生更有效率的程式碼，以重新排序或合併作業，並使用簡化不是標準所允許的代數轉換。

## <a name="syntax"></a>語法

> **/fp：**[**精確**  |  **嚴格**地  |  **快速**  |  **（**[] 除外） **-** ]

### <a name="arguments"></a>引數

#### <a name="precise"></a>地

根據預設，編譯器會使用 `/fp:precise` 行為。

在 `/fp:precise` 編譯器底下，會在產生並優化目的電腦的物件程式碼時，保留浮點程式碼的來源運算式順序和舍入屬性。 編譯器會在運算式評估期間的四個特定點四捨五入至原始程式碼精確度：在 typecasts 時，將浮點引數傳遞至函式呼叫，以及從函式呼叫傳回浮點值時。 中繼計算可能會以電腦的精確度來執行。 Typecasts 可以用來明確地迴圈中繼計算。

編譯器不會在浮點運算式（例如重新關聯或散發）上執行代數轉換，除非保證轉換會產生位相同的結果。
牽涉到特殊值（NaN、+ 無限大、-無限大、-0.0）的運算式會根據 IEEE-754 規格進行處理。 例如， `x != x` **`true`** 如果 x 是 NaN，則會評估為。 浮點*縮寫*（也就是結合浮點運算的機器指令）可能會在下產生 `/fp:precise` 。

編譯器會產生要在[預設浮點環境](#the-default-floating-point-environment)中執行的程式碼，並假設在執行時間不會存取或修改浮點環境。 也就是說，它會假設程式碼不會取消遮罩浮點例外狀況、讀取或寫入浮點狀態暫存器，或變更舍入模式。

如果您的浮點程式碼不會相依于浮點語句中的作業和運算式順序（例如，如果您不在意是否 `a * b + a * c` 計算為 `(b + c) * a` 或 `2 * a` `a + a` ），請考慮採用[/fp： fast](#fast)選項，這可以產生更快、更有效率的程式碼。 如果您的程式碼都取決於作業和運算式的順序，並存取或改變浮點環境（例如，若要變更舍入模式或捕捉浮點例外狀況），請使用[/fp： strict](#strict)。

#### <a name="strict"></a>strict

`/fp:strict`具有類似于 `/fp:precise` 的行為，也就是說，編譯器會在產生並優化目的電腦的物件程式碼時，保留浮點程式碼的來源順序和舍入屬性，並在處理特殊值時觀察標準。 此外，程式可以在執行時間安全地存取或修改浮點環境。

在之下 `/fp:strict` ，編譯器會產生程式碼，讓程式可以安全地取消遮罩浮點例外狀況、讀取或寫入浮點狀態暫存器，或變更舍入模式。 在運算式評估期間，它會四捨五入為四個特定點的原始程式碼精確度：在 typecasts 時、將浮點引數傳遞至函式呼叫，以及從函式呼叫傳回浮點值時。 中繼計算可能會以電腦的精確度來執行。 Typecasts 可以用來明確地迴圈中繼計算。 編譯器不會在浮點運算式（例如重新關聯或散發）上執行代數轉換，除非保證轉換會產生位相同的結果。 牽涉到特殊值（NaN、+ 無限大、-無限大、-0.0）的運算式會根據 IEEE-754 規格進行處理。 例如， `x != x` **`true`** 如果 x 是 NaN，則會評估為。 在底下不會產生浮點縮寫 `/fp:strict` 。

`/fp:strict`計算的成本高於， `/fp:precise` 因為編譯器必須插入額外的指示來攔截例外狀況，並允許程式在執行時間存取或修改浮點環境。 如果您的程式碼未使用這項功能，但需要原始程式碼排序和舍入，或依賴特殊值，請使用 `/fp:precise` 。 否則，請考慮使用 `/fp:fast` ，這可以產生更快速且更小的程式碼。

#### <a name="fast"></a>快速

`/fp:fast`選項可讓編譯器重新排列、結合或簡化浮點作業，以優化浮點程式碼的速度和空間。 編譯器可能會在指派語句、typecasts 或函式呼叫中省略進位。 它可能會重新排序作業或執行代數轉換（例如，使用關聯和分配法），即使這類轉換會導致明顯不同的舍入行為。 由於這項增強的優化，某些浮點計算的結果可能會與其他選項所產生的不同 `/fp` 。 特殊值（NaN、+ 無限大、-無限大、-0.0）可能不會根據 IEEE-754 標準傳播或嚴格行為。 可能會在底下產生浮點縮寫 `/fp:fast` 。 編譯器仍然受下的基礎架構所限制 `/fp:fast` ，而且可以透過使用[/arch](arch-minimum-cpu-architecture.md)選項來提供其他優化。

在之下 `/fp:fast` ，編譯器會產生要在預設浮點環境中執行的程式碼，並假設在執行時間不會存取或修改浮點環境。 也就是說，它會假設程式碼不會取消遮罩浮點例外狀況、讀取或寫入浮點狀態暫存器，或變更舍入模式。

`/fp:fast`適用于不需要嚴格的原始程式碼排序和舍入浮點運算式的程式，而且不依賴標準規則來處理 NaN 之類的特殊值。 如果您的浮點程式碼需要保留原始程式碼順序和舍入，或依賴特殊值的標準行為，請使用[/fp：精確](#precise)。 如果您的程式碼存取或修改浮點環境以變更進位模式、取消遮罩浮點例外狀況，或檢查浮點狀態，請使用[/fp： strict](#strict)。

#### <a name="except"></a>但是

`/fp:except`選項會產生程式碼，以確保任何取消遮罩的浮點例外狀況會在其發生的確切位置引發，而且不會引發任何額外的浮點例外狀況。 根據預設， `/fp:strict` 選項會啟用 `/fp:except` ，而不是 `/fp:precise` 。 `/fp:except`選項與不相容 `/fp:fast` 。 此選項可以由美國明確停用 `/fp:except-` 。

請注意，不 `/fp:except` 會自行啟用任何浮點例外狀況，但程式必須啟用浮點例外狀況。 如需如何啟用浮點例外狀況的詳細資訊，請參閱[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 。

## <a name="remarks"></a>備註

`/fp`可以在相同的編譯器命令列中指定多個選項。 只有其中一個 `/fp:strict` 、 `/fp:fast` 和 `/fp:precise` 選項可以同時生效。 如果在命令列上指定了一個以上的選項，則較新的選項會優先，而編譯器會產生警告。 `/fp:strict`和 `/fp:except` 選項與不相容 `/clr` 。

[/Za](za-ze-disable-language-extensions.md) （ANSI 相容性）選項與不相容 `/fp` 。

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>使用編譯器指示詞來控制浮點行為

編譯器提供三個 pragma 指示詞來覆寫在命令列上指定的浮點行為： [float_control](../../preprocessor/float-control.md)、 [fenv_access](../../preprocessor/fenv-access.md)和[fp_contract](../../preprocessor/fp-contract.md)。 您可以使用這些指示詞，在函式層級控制浮點行為，而不是在函數中。 請注意，這些指示詞不會直接對應到 `/fp` 選項。 下表顯示 `/fp` options 和 pragma 指示詞彼此對應的方式。 如需詳細資訊，請參閱個別選項和 pragma 指示詞的檔。

||float_control （精確）|float_control （除外）|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|關|關|關|on|
|`/fp:precise`|on|關|關|on|
|`/fp:strict`|on|on|on|關|

### <a name="the-default-floating-point-environment"></a>預設的浮點環境

初始化進程時，會設定*預設的浮點環境*。 此環境會遮罩所有浮點例外狀況，將進位模式設定為四捨五入到最接近的（ `FE_TONEAREST` ），保留偏低（denormal）值，針對、和值使用預設的有效位數有效位數（尾數）， **`float`** **`double`** **`long double`** 並在支援的情況下，將無限大控制項設定為預設的仿射模式。

### <a name="floating-point-environment-access-and-modification"></a>浮點環境存取和修改

Microsoft Visual C++ 執行時間會提供幾個函式來存取和修改浮點環境。 其中包括[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)、 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)和[_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)及其變體。 若要在您的程式碼存取或修改浮點環境時確保正確的程式列為， `fenv_access` 必須透過 `/fp:strict` 選項或使用 pragma 來啟用，這些函式才會 `fenv_access` 有任何作用。 當未 `fenv_access` 啟用時，存取或修改浮點環境可能會導致非預期的程式列為：程式碼可能不會接受對浮點環境所要求的變更; 浮點狀態暫存器可能不會報告預期或目前的結果，而且可能會發生非預期的浮點例外狀況，或可能不會發生浮點例外狀況。

當您的程式碼存取或修改浮點環境時，您必須謹慎地結合程式碼，其中 `fenv_access` 已啟用但未啟用的程式碼 `fenv_access` 。 在 `fenv_access` 未啟用的程式碼中，編譯器會假設平臺預設浮點環境已生效，而且不會存取或修改浮點狀態。 我們建議您在控制傳送至未啟用的函式之前，先將本機浮點環境儲存並還原為其預設狀態 `fenv_access` 。 這個範例會示範如何 `float_control` 設定和還原 pragma：

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>浮點進位模式

在和編譯器底下，會 `/fp:precise` `/fp:fast` 產生要在預設浮點環境中執行的程式碼，並假設環境不會在執行時間存取或修改。 也就是說，它會假設程式碼不會取消遮罩浮點例外狀況、讀取或寫入浮點狀態暫存器，或變更舍入模式。  不過，某些程式需要改變浮點環境。 例如，此範例會藉由改變浮點舍入模式來計算浮點乘法的誤差界限：

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

因為編譯器會在下假設預設的浮點環境 `/fp:fast` ， `/fp:precise` 所以您可以隨意忽略對的呼叫 `_controlfp_s` 。 例如，當使用 `/O2` 和 `/fp:precise` 針對 x86 架構來編譯時，不會計算界限，而且範例程式會輸出：

```Output
cLower = -inf
cUpper = -inf
```

當 x86 架構的和同時編譯時 `/O2` `/fp:strict` ，範例程式會輸出：

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>浮點特殊值

在 `/fp:precise` 和底下 `/fp:strict` ，牽涉到特殊值（NaN、+ 無限大、-無限大、-0.0）的運算式會根據 IEEE-754 規格來運作。 在之下 `/fp:fast` ，這些特殊值的行為可能會與 IEEE-754 不一致。

這個範例會示範下列各項特殊值的不同行為 `/fp:precise` `/fp:strict` `/fp:fast` ：

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

當使用 `/O2` `/fp:precise` 或 `/O2` `/fp:strict` 針對 x86 架構編譯時，輸出會與 IEEE-754 規格一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

`/O2` `/fp:fast` 針對 x86 架構使用進行編譯時，輸出與 IEEE-754 不一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>浮點代數轉換

在 `/fp:precise` 和下 `/fp:strict` ，除非保證轉換會產生位相同的結果，否則編譯器不會執行數學轉換。 編譯器可能會在下執行這類轉換 `/fp:fast` 。 例如，範例函式 `a * b + a * c` 中的運算式 `algebraic_transformation` 可能會編譯成 `a * (b + c)` 之下的 `/fp:fast` 。 這類轉換不會在或之下執行 `/fp:precise` `/fp:strict` ，而編譯器會產生 `a * b + a * c` 。

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>浮點明確轉換點

在 `/fp:precise` 和下 `/fp:strict` ，編譯器會在運算式評估期間的四個特定點進位至原始程式碼精確度：在 typecasts 時、將浮點引數傳遞至函式呼叫，以及從函式呼叫傳回浮點值時。 Typecasts 可以用來明確地迴圈中繼計算。 在之下 `/fp:fast` ，編譯器不會在這些點產生明確的轉換，以保證原始程式碼的精確度。 這個範例會示範不同選項下的行為 `/fp` ：

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

當使用或來編譯時 `/O2` `/fp:precise` `/O2` `/fp:strict` ，您可以看到明確型別轉換會在轉換和在 x64 架構產生的程式碼中的函式傳回點插入：

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

在 `/O2` `/fp:fast` 產生的程式碼底下已簡化，因為所有類型轉換都已優化：

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +** 程式  >  **代碼產生**] 屬性頁。

1. 修改 [**浮點模型**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
