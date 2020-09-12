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
ms.openlocfilehash: 7a8ae885bbbf00ae916505bf5df646b32268a17a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040908"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (指定浮點數行為)

指定編譯器如何處理浮點運算式、優化和例外狀況。 **/Fp**選項指定產生的程式碼是否允許浮點環境變更舍入模式、例外狀況遮罩和偏低行為，以及浮點數狀態檢查是否傳回目前的精確結果。 它會控制編譯器是否會產生可維護來源作業和運算式順序的程式碼，並符合 NaN 傳播的標準，或是產生更有效率的程式碼，以重新排列或合併作業，並使用簡化標準不允許的代數轉換。

## <a name="syntax"></a>語法

> **/fp：**[**精確**  |  **嚴格**的  |  **快速**，  |  **例外**[ **-** ]]

### <a name="arguments"></a>引數

#### <a name="precise"></a>精確

根據預設，編譯器會使用 `/fp:precise` 行為。

`/fp:precise`編譯器會在產生並優化目的電腦的目的程式代碼時，保留浮點程式碼的來源運算式順序和舍入屬性。 編譯器會在運算式評估期間的四個特定點四捨五入為原始程式碼精確度：在指派時、于 typecasts、將浮點引數傳遞至函式呼叫時，以及從函式呼叫傳回浮點值時。 中繼計算可能會以機器的精確度來執行。 Typecasts 可以用來明確地舍入中繼計算。

除非保證轉換會產生位相同的結果，否則編譯器不會在浮點運算式（例如重新關聯或分佈）上執行代數轉換。
牽涉到特殊值的運算式 (NaN、+ 無限大、-無限大、-0.0) 會根據 IEEE-754 規格進行處理。 例如， `x != x` **`true`** 如果 x 是 NaN，則會評估為。 浮點數 *縮寫*，也就是結合浮點運算的機器指令，可能會在底下產生 `/fp:precise` 。

編譯器會產生要在 [預設浮點環境](#the-default-floating-point-environment) 中執行的程式碼，並假設在執行時間不會存取或修改浮點環境。 也就是說，它會假設程式碼不會取消遮罩浮點例外狀況、讀取或寫入浮點數狀態暫存器，或變更舍入模式。

如果您的浮點程式碼不相依于浮點數語句中的運算和運算式順序 (例如，如果您不在意是否 `a * b + a * c` 計算為 `(b + c) * a` 或 `2 * a` `a + a`) ，請考慮 [/fp： fast](#fast) 選項，這可以產生更快、更有效率的程式碼。 如果您的程式碼都取決於作業和運算式的順序，以及存取或改變浮點環境 (例如，若要變更舍入模式或) 攔截浮點例外狀況，請使用 [/fp： strict](#strict)。

#### <a name="strict"></a>strict

`/fp:strict` 具有類似的行為 `/fp:precise` ，也就是，編譯器會在產生並優化目的電腦的目的程式代碼時，保留浮點程式碼的來源排序和舍入屬性，並在處理特殊值時觀察標準。 此外，程式可以在執行時間安全地存取或修改浮點環境。

在下 `/fp:strict` ，編譯器會產生程式碼，該程式碼可讓程式安全地取消遮罩浮點例外狀況、讀取或寫入浮點狀態暫存器，或變更舍入模式。 它會在運算式評估期間的四個特定點四捨五入為原始程式碼精確度：在指派時、于 typecasts、將浮點引數傳遞至函式呼叫時，以及從函式呼叫傳回浮點值時。 中繼計算可能會以機器的精確度來執行。 Typecasts 可以用來明確地舍入中繼計算。 除非保證轉換會產生位相同的結果，否則編譯器不會在浮點運算式（例如重新關聯或分佈）上執行代數轉換。 牽涉到特殊值的運算式 (NaN、+ 無限大、-無限大、-0.0) 會根據 IEEE-754 規格進行處理。 例如， `x != x` **`true`** 如果 x 是 NaN，則會評估為。 不會產生浮點數縮寫 `/fp:strict` 。

`/fp:strict` 運算的成本比 `/fp:precise` 編譯器必須插入額外的指示來攔截例外狀況，並允許程式在執行時間存取或修改浮點數環境更高。 如果您的程式碼未使用這項功能，但需要原始程式碼順序和舍入，或是依賴特殊值，請使用 `/fp:precise` 。 否則，請考慮使用 `/fp:fast` ，這可以產生更快速且較小的程式碼。

#### <a name="fast"></a>快速

`/fp:fast`選項可讓編譯器重新排列、合併或簡化浮點運算，以優化浮點程式碼的速度和空間。 編譯器可能會省略指派語句、typecasts 或函式呼叫的舍入。 它可能會重新排序作業或執行代數轉換（例如，藉由使用關聯和分配法則），即使這類轉換導致明顯不同的舍入行為也是如此。 由於這個增強的優化，某些浮點運算的結果可能會與其他選項所產生的不同 `/fp` 。  (NaN、+ 無限大、-無限大、-0.0) 的特殊值可能不會根據 IEEE-754 標準傳播或行為嚴格。 可能會產生浮點數縮寫 `/fp:fast` 。 編譯器仍受下基礎架構的系結 `/fp:fast` ，而且可能會透過使用 [/arch](arch-minimum-cpu-architecture.md) 選項來提供額外的優化。

在下 `/fp:fast` ，編譯器會產生要在預設浮點環境中執行的程式碼，並假設在執行時間不會存取或修改浮點環境。 也就是說，它會假設程式碼不會取消遮罩浮點例外狀況、讀取或寫入浮點數狀態暫存器，或變更舍入模式。

`/fp:fast` 適用于不需要嚴格的原始程式碼排序和舍入浮點運算式的程式，也不依賴處理特殊值（例如 NaN）的標準規則。 如果您的浮點程式碼需要保留原始程式碼順序和舍入，或是依賴特殊值的標準行為，請使用 [/fp：精確](#precise)。 如果您的程式碼存取或修改浮點環境以變更舍入模式、取消遮罩浮點例外狀況，或檢查浮點狀態，請使用 [/fp： strict](#strict)。

#### <a name="except"></a>除了

`/fp:except`選項會產生程式碼，以確保任何未遮罩的浮點例外狀況會在其發生的確切位置引發，而且不會引發任何額外的浮點例外狀況。 依預設， `/fp:strict` 選項會啟用 `/fp:except` ，而不 `/fp:precise` 會啟用。 `/fp:except`選項與不相容 `/fp:fast` 。 您可以明確停用此選項 `/fp:except-` 。

請注意，不 `/fp:except` 會自行啟用任何浮點例外狀況，但是程式必須有這個例外狀況，才能啟用浮點例外狀況。 如需如何啟用浮點例外狀況的詳細資訊，請參閱 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) 。

## <a name="remarks"></a>備註

您 `/fp` 可以在相同的編譯器命令列中指定多個選項。 `/fp:strict`一次只能有、和選項的其中一個 `/fp:fast` `/fp:precise` 作用。 如果在命令列上指定了以上其中一個選項，則會優先使用較新的選項，而編譯器會產生警告。 `/fp:strict`和 `/fp:except` 選項與不相容 `/clr` 。

[/Za](za-ze-disable-language-extensions.md) (ANSI 相容性) 選項與不相容 `/fp` 。

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>使用編譯器指示詞來控制浮點行為

編譯器提供三個 pragma 指示詞，以覆寫命令列上指定的浮點行為： [float_control](../../preprocessor/float-control.md)、 [fenv_access](../../preprocessor/fenv-access.md)和 [fp_contract](../../preprocessor/fp-contract.md)。 您可以使用這些指示詞，在函式層級（而不是在函式內）控制浮點行為。 請注意，這些指示詞不會直接對應到 `/fp` 選項。 下表顯示 options 和 pragma 指示詞如何彼此 `/fp` 對應。 如需詳細資訊，請參閱個別選項和 pragma 指示詞的檔。

| 選項 | float_control (精確)  | float_control (除外)  | fenv_access | fp_contract |
|-|-|-|-|-|
|`/fp:fast`|關|關|關|on|
|`/fp:precise`|on|關|關|on|
|`/fp:strict`|on|on|on|關|

### <a name="the-default-floating-point-environment"></a>預設浮動點環境

當處理常式初始化時，會設定 *預設的浮點環境* 。 此環境會遮罩所有的浮點例外狀況、將舍入模式設定為四捨五入至最接近的 (`FE_TONEAREST`) 、保留偏低 (denormal) 值、使用有效位數的預設有效位數 (的 **`float`** 、 **`double`** 和 **`long double`** 值，以及在支援的位置，將無限大控制項設定為預設仿射模式。

### <a name="floating-point-environment-access-and-modification"></a>浮點環境存取和修改

Microsoft Visual C++ 執行時間提供數個函數，以存取和修改浮點環境。 這些包含 [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)、 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)和 [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) 及其變異。 若要在您的程式碼存取或修改浮點數環境時確保正確的程式列為， `fenv_access` 則必須透過選項或使用 pragma 來啟用這些函式，這些函式 `/fp:strict` 才會 `fenv_access` 有任何作用。 如果 `fenv_access` 未啟用，則存取或修改浮點數環境可能會導致非預期的程式列為：程式碼可能無法接受要求的浮點環境變更; 浮點數暫存器可能不會報告預期或目前的結果，而且可能會發生未預期的浮點例外狀況，或可能不會發生預期的浮點例外狀況。

當您的程式碼存取或修改浮點數環境時，當您將已 `fenv_access` 啟用的程式碼與未啟用的程式碼合併時，必須特別小心 `fenv_access` 。 在 `fenv_access` 未啟用的程式碼中，編譯器會假設平臺預設浮點環境有效，且不會存取或修改浮點狀態。 建議您先將本機浮點環境儲存並還原為預設狀態，然後再將控制項傳送至未啟用的函式 `fenv_access` 。 這個範例會示範如何 `float_control` 設定和還原 pragma：

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>浮點數舍入模式

在 `/fp:precise` 和編譯器下， `/fp:fast` 編譯器會產生要在預設浮點環境中執行的程式碼，並假設在執行時間不會存取或修改環境。 也就是說，它會假設程式碼不會取消遮罩浮點例外狀況、讀取或寫入浮點數狀態暫存器，或變更舍入模式。  但是，某些程式必須改變浮點環境。 例如，此範例會藉由改變浮點數舍入模式來計算浮點數乘法的誤差界線：

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

由於編譯器會假設下的預設浮點數環境 `/fp:fast` ，因此 `/fp:precise` 可以自由地忽略對的呼叫 `_controlfp_s` 。 例如，使用 `/O2` 和 x86 架構編譯時， `/fp:precise` 不會計算界限，而範例程式會輸出：

```Output
cLower = -inf
cUpper = -inf
```

使用 `/O2` 和 `/fp:strict` x86 架構編譯時，範例程式會輸出：

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>浮點數特殊值

在 `/fp:precise` 和之下 `/fp:strict` ，牽涉到特殊值的運算式 (NaN、+ 無限大、-無限大、-0.0) 根據 IEEE-754 規格的行為。 在下 `/fp:fast` ，這些特殊值的行為可能會與 IEEE-754 不一致。

這個範例會示範下的特殊值和的不同行為 `/fp:precise` `/fp:strict` `/fp:fast` ：

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

當使用 `/O2` `/fp:precise` 或 `/O2` `/fp:strict` x86 架構編譯時，輸出會與 IEEE-754 規格一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

當 `/O2` `/fp:fast` 針對 x86 架構編譯時，輸出與 IEEE-754 不一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>浮點數代數轉換

在 `/fp:precise` 和下 `/fp:strict` ，除非保證轉換產生位相同的結果，否則編譯器不會執行數學轉換。 編譯器可能會在下執行這類轉換 `/fp:fast` 。 例如，範例函式 `a * b + a * c` 中的運算式 `algebraic_transformation` 可能會編譯成 `a * (b + c)` 下的 `/fp:fast` 。 這類轉換不會在或之下執行 `/fp:precise` `/fp:strict` ，而編譯器會產生 `a * b + a * c` 。

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>浮點數明確轉換點

在 `/fp:precise` 和下 `/fp:strict` ，編譯器會在運算式評估期間的四個特定點四捨五入為原始程式碼精確度：在指派時、于 typecasts、將浮點引數傳遞至函式呼叫時，以及從函式呼叫傳回浮點值時。 Typecasts 可以用來明確地舍入中繼計算。 在下 `/fp:fast` ，編譯器不會在這些點產生明確的轉換，以保證原始程式碼的精確度。 這個範例會示範不同選項下的行為 `/fp` ：

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

使用或編譯時 `/O2` `/fp:precise` `/O2` `/fp:strict` ，您可以看到在 x64 架構的產生程式碼中，轉換和函數傳回點都插入了明確的型別轉換：

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

`/O2` `/fp:fast` 已簡化產生的程式碼，因為所有類型轉換都已優化：

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**  >  **C/c + +** 程式  >  **代碼產生**] 屬性頁。

1. 修改 **浮動點模型** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
