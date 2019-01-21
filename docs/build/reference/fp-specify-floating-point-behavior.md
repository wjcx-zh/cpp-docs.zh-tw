---
title: /fp （指定浮點數行為）
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
ms.openlocfilehash: 77e6d0c97f1d0381fe32ae23f8d7e8bd02ddf219
ms.sourcegitcommit: 22f7c4a9b4fc2158fb5283810f15275803cafe10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417638"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp （指定浮點數行為）

指定編譯器如何處理浮點運算式、 最佳化，以及例外狀況。 **/Fp**選項會指定產生的程式碼是否允許捨入模式、 例外狀況遮罩和 subnormal 行為的浮點環境變更和浮點狀態檢查是傳回目前已經過正確結果。 它所控制編譯器是否會產生程式碼，會保留原始檔作業與排序運算式，並符合標準的 NaN 傳播，或如果它改為會產生更有效率的程式碼，可能會重新排列或合併作業並使用簡化標準不允許的代數轉換。

## <a name="syntax"></a>語法

> **/fp:**[**precise** | **strict** | **fast** | **except**[**-**]]

### <a name="arguments"></a>引數

#### <a name="precise"></a>精確

根據預設，編譯器會使用 **/fp： 精確**行為。

底下 **/fp： 精確**編譯器會保留排序和捨入浮點程式碼的屬性，當它產生並最佳化物件的目標機器的程式碼的來源運算式。 運算式評估期間，編譯器會四捨五入到四個特定時間點的來源的程式碼有效位數： 在指派，在類型轉換，，和浮點引數傳遞至函式呼叫時的浮點值時就會傳回從函式呼叫。 中繼計算可能會執行在機器有效位數。 類型轉換可以用來明確地將中繼計算。

編譯器不會執行代數轉換浮點數的運算式，例如重新關聯或發佈，除非轉換保證會產生位元的相同結果。
根據 IEEE 754 規格處理涉及特殊值 （NaN、 + infinity、-infinity，-0.0） 的運算式。 例如，`x != x`評估為 **，則為 true**如果 x 為 NaN。 浮點*縮寫*，也就是浮點作業，結合的機器指示下，可能會產生 **/fp： 精確**。

編譯器會產生要執行的程式碼[預設的浮點環境](#the-default-floating-point-environment)和假設的浮點環境無法存取或在執行階段修改。 也就是說，它會假設，程式碼未取消遮罩浮點例外狀況、 讀取或寫入浮點狀態暫存器，或變更捨入模式。

如果您的浮點程式碼無關的作業和浮點陳述式中的運算式 (例如，如果您不在乎是否`a * b + a * c`的計算方式為`(b + c) * a`或`2 * a`做為`a + a`)，請考慮[/fp: fast](#fast)選項，可以產生更快、 更有效率的程式碼。 如果您的程式碼同時相依於運算和運算式，並存取或改變 （例如，若要變更捨入模式，或設陷浮點例外狀況） 的浮點環境，使用[/fp: strict](#strict)。

#### <a name="strict"></a>strict

**/fp: strict**行為類似於 **/fp： 精確**，也就是編譯器會保留來源以及浮點程式碼產生和最佳化時的捨入的屬性物件的目標機器的程式碼並處理特殊的值時，會遵守標準。 此外，程式可能會安全地存取或修改在執行階段的浮點環境。

底下 **/fp: strict**，編譯器會產生程式碼，讓程式可以安全地取消遮罩浮點例外狀況、 讀取或寫入浮點狀態暫存器，或變更捨入模式。 它會捨入為四個特定時間點的來源的程式碼有效位數運算式的評估期間： 在指派，在類型轉換，，和浮點引數傳遞至函式呼叫時的浮點值時就會傳回從函式呼叫。 中繼計算可能會執行在機器有效位數。 類型轉換可以用來明確地將中繼計算。 編譯器不會執行代數轉換浮點數的運算式，例如重新關聯或發佈，除非轉換保證會產生位元的相同結果。 根據 IEEE 754 規格處理涉及特殊值 （NaN、 + infinity、-infinity，-0.0） 的運算式。 例如，`x != x`評估為 **，則為 true**如果 x 為 NaN。 下不會產生浮點數的縮寫 **/fp: strict**。

**/fp: strict**耗費成本高於 **/fp： 精確**因為編譯器必須插入以攔截例外狀況，並允許程式的存取或修改的浮點環境的其他指示執行階段。 如果您的程式碼不會使用這項功能，但需要來源的程式碼順序和捨入，或依賴特殊值，使用 **/fp： 精確**。 否則，請考慮使用 **/fp: fast**，，可能會產生更快更小的程式碼。

#### <a name="fast"></a>快速

**/Fp: fast**選項可讓編譯器重新排列、 合併或簡化以最佳化浮點程式碼的速度和空間的浮點運算。 編譯器可能會省略捨入在指派陳述式、 類型轉換或函式呼叫。 它可能重新排列運算或執行代數轉換，例如，使用關聯和分散的法規，即使這類轉換會導致明顯不同的捨入行為。 此增強的最佳化，因為某些浮點運算的結果可能與不同所產生的其他 **/fp**選項。 特殊值 （NaN、 + infinity、-infinity，-0.0） 不會傳播，或根據 IEEE 754 標準嚴格的行為。 下，可能會產生浮點數的縮寫 **/fp: fast**。 編譯器仍受限於基礎架構底下 **/fp: fast**，和其他最佳化可透過善用[/arch](../../build/reference/arch-minimum-cpu-architecture.md)選項。

底下 **/fp: fast**，編譯器會產生要在預設的浮點環境中執行的程式碼，並假設不存取的浮點環境，或在執行階段修改。 也就是說，它會假設，程式碼未取消遮罩浮點例外狀況、 讀取或寫入浮點狀態暫存器，或變更捨入模式。

**/fp: fast**適合的程式不需要嚴格的來源的程式碼順序和捨入浮點運算式，並不依賴標準的規則，以便處理特殊的值，例如 NaN。 如果您的浮點程式碼需要保留順序和捨入的原始程式碼，或依賴的特殊值，使用標準行為[/fp： 精確](#precise)。 如果您的程式碼可以存取或修改的浮點環境，若要變更捨入模式，取消遮罩浮點例外狀況，或檢查浮點狀態，請使用[/fp: strict](#strict)。

#### <a name="except"></a>except

**/Fp： 除了**選項會產生可確保在處發生，確切的時間點，會引發任何取消遮罩浮點例外狀況，而且會引發任何其他的浮點例外狀況的程式碼。 根據預設， **/fp: strict**選項可讓 **/fp： 除了**，和 **/fp： 精確**則否。 **/Fp： 除了**選項不相容 **/fp: fast**。 此選項可以明確停用我們的 **/fp： 除了-**。

請注意， **/fp： 除了**不會啟用任何浮點例外狀況本身，但其實需要啟用浮點例外狀況的程式。 請參閱[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)如需如何啟用浮點例外狀況的資訊。

## <a name="remarks"></a>備註

多個 **/fp**相同的編譯器命令列中，您可以指定選項。 只有其中一個 **/fp: strict**， **/fp: fast**，並 **/fp： 精確**選項可以實際上是一次。 如果以上其中一個選項指定命令列上，更新版本的選項會優先，編譯器會產生警告。 **/Fp: strict**並 **/fp： 除了**選項不相容於 **/clr**。

[/Za](../../build/reference/za-ze-disable-language-extensions.md) （ANSI 相容性） 選項不相容 **/fp**。

### <a name="using-pragmas-to-control-floating-point-behavior"></a>使用 Pragma 控制浮點數行為

編譯器會提供三個的 pragma 指示詞，來覆寫在命令列上指定的浮點行為： [float_control](../../preprocessor/float-control.md)， [fenv_access](../../preprocessor/fenv-access.md)，和[fp_contract](../../preprocessor/fp-contract.md). 您可以使用這些 pragma 控制函式層級，不會在函式內的浮點數行為。 請注意這些 pragma 並不會直接的對應 **/fp**選項。 下表顯示如何 **/fp**互相對應的選項和 pragma。 如需詳細資訊，請參閱個別選項和 pragma 的文件。

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|**/fp:fast**|關閉|關閉|關閉|於|
|**/fp:precise**|於|關閉|關閉|於|
|**/fp:except**|於|於|於|關閉|

### <a name="the-default-floating-point-environment"></a>預設浮點環境

初始化處理程序時，*預設的浮點環境*設定。 這種環境會遮罩所有浮點例外狀況、 將捨入模式設定為四捨五入到最接近 (`FE_TONEAREST`)，會保留 subnormal （異常） 值，用於有效數字 （尾數） 的預設有效位數**float**， **雙**，並**長雙精度**值，然後支援，將無限大控制項設定為預設的仿射模式。

### <a name="floating-point-environment-access-and-modification"></a>浮點環境存取和修改

Microsoft Visual c + + 執行階段會提供數個函數來存取和修改的浮點環境。 其中包括[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)， [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)，並[_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)及其變體。 若要確認正確的程式行為，當您的程式碼可以存取或修改的浮點環境`fenv_access`必須啟用，請藉由 **/fp: strict**選項，或藉由使用`fenv_access`程式，這些函式來有任何作用。 當`fenv_access`是未啟用，存取或修改的浮點環境可能會導致非預期的程式行為： 程式碼可能不會接受要求的變更，到浮點環境，可能不會報告的浮點狀態暫存器預期或目前的結果;和非預期的浮點例外狀況可能會發生，或可能不會發生預期的浮點例外狀況。

當您的程式碼可以存取或修改的浮點環境時，您必須非常小心結合程式碼時，`fenv_access`使用程式碼，並沒有啟用`fenv_access`啟用。 在程式碼中其中`fenv_access`未啟用，則編譯器會假設平台預設值的浮點環境處於作用中，而且無法存取或修改浮點狀態。 我們建議您儲存，並在本機的浮點環境還原為其預設狀態，控制權會轉移到沒有函式之前`fenv_access`啟用。 此範例示範如何`float_control`pragma 可設定及還原：

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>浮點捨入模式

在這兩 **/fp： 精確**並 **/fp: fast**編譯器會產生要在預設的浮點環境中執行的程式碼，並假設不存取的環境，或在執行階段修改。 也就是說，它會假設，程式碼未取消遮罩浮點例外狀況、 讀取或寫入浮點狀態暫存器，或變更捨入模式。  不過，有些程式需要改變的浮點環境。 比方說，此範例會計算誤差界限的浮點數的乘法改變浮點四捨五入模式：

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

因為編譯器會假設預設的浮點環境下的 **/fp: fast**並 **/fp： 精確**沒有忽略呼叫`_controlfp_s`。 例如，當編譯使用這兩個 **/o2**並 **/fp： 精確**適用於 x86 架構，不會計算範圍，以及範例程式會輸出：

```Output
cLower = -inf
cUpper = -inf
```

同時與編譯時 **/o2**並 **/fp: strict**適用於 x86 架構中，範例程式會輸出：

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>浮點數的特殊值

底下 **/fp： 精確**並 **/fp: strict**，牽涉到特殊值 （NaN、 + infinity、-infinity，-0.0） 的運算式的行為會根據 IEEE 754 規格。 底下 **/fp: fast**，這些特殊值的行為可能與 IEEE-754 不一致。

這個範例會示範不同的行為的特殊值 **/fp： 精確**， **/fp: strict**並 **/fp: fast**:

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

編譯時 **/o2** **/fp： 精確**或是 **/o2** **/fp: strict**適用於 x86 架構，輸出會與 IEEE-754 一致規格：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

編譯時 **/o2** **/fp: fast**適用於 x86 架構，輸出不是與 IEEE-754 一致：

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>浮點數的代數轉換

底下 **/fp： 精確**並 **/fp: strict**，編譯器不會執行數學轉換，除非轉換保證會產生位元的相同結果。 編譯器可能會執行這類轉換之下 **/fp: fast**。 例如，運算式`a * b + a * c`範例函式中`algebraic_transformation`可能會編譯成`a * (b + c)`之下 **/fp: fast**。 這類轉換不執行底下 **/fp： 精確**或 **/fp: strict**，編譯器可能會產生`a * b + a * c`。

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>浮點數的明確轉換的點

底下 **/fp： 精確**並 **/fp: strict**，運算式評估期間，編譯器會四捨五入到四個特定時間點的來源的程式碼有效位數： 在指派，在類型轉換時的浮點引數會傳遞至函式呼叫時，並從函式呼叫會傳回浮點值。 類型轉換可以用來明確地將中繼計算。 底下 **/fp: fast**，編譯器不會產生明確的轉型，在這些點，以確保來源的程式碼的有效位數。 這個範例會示範在不同的行為 **/fp**選項：

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

編譯使用時 **/o2** **/fp： 精確**或是 **/o2** **/fp: strict**，您所見，插入的明確類型轉換是在類型轉換，並在函式傳回點產生的程式碼，適用於 x64 架構：

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

底下 **/o2** **/fp: fast**產生的程式碼已經過簡化，因為所有的型別轉換最佳化改變了：

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **程式碼產生**屬性頁。

1. 修改**浮點模型**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](compiler-options.md)<br/>
[設定編譯器選項](setting-compiler-options.md)<br/>
[Microsoft Visual c + + 浮點最佳化](floating-point-optimization.md)<br/>
