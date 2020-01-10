---
title: /arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: b1e5501f6edd3eb016395380ff476250c0c388b9
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816322"
---
# <a name="arch-x86"></a>/arch (x86)

在 x86 上，為程式碼產生指定架構。 另請參閱[/arch （x64）](arch-x64.md)和[/arch （ARM）](arch-arm.md)。

## <a name="syntax"></a>語法

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>引數

**/arch： IA32**<br/>
指定沒有增強的指令，同時指定用於浮點數計算的 x87。

**/arch： SSE**<br/>
啟用 SSE 指令的使用。

**/arch： SSE2**<br/>
啟用 SSE2 指令的使用。 這是在 x86 平臺上的預設指示（如果未指定 **/arch**選項）。

**/arch:AVX**<br/>
啟用 Intel Advanced Vector Extensions 指令的使用。

**/arch： AVX2**<br/>
啟用 Intel Advanced Vector Extensions 2 指令的使用。

**/arch： AVX512**<br/>
啟用 Intel Advanced Vector Extensions 512 指示的使用。

## <a name="remarks"></a>備註

**/Arch**選項會啟用或停用特定指令集延伸模組的使用，特別是針對向量計算，適用于 INTEL 和 AMD 的處理器。 一般來說，最新引進的處理器可能支援較舊處理器支援的額外延伸模組，但您應該參閱特定處理器的檔，或使用 __ 測試指令集延伸模組支援使用指令集延伸模組執行程式碼之前的 [cpuid](../../intrinsics/cpuid-cpuidex.md)。

**/arch**只會影響原生函式的程式碼產生。 當您使用[/clr](clr-common-language-runtime-compilation.md)進行編譯時， **/arch**不會影響 managed 函式的程式碼產生。

**/Arch**選項會參考具有下列特性的指令集延伸模組：

- **IA32**是舊版32位 x86 指令集，不含任何向量運算，而且會針對浮點計算使用 x87。

- **SSE**允許以最多四個單精確度浮點值的向量來計算。 也加入對應的純量浮點指示。

- **SSE2**允許以單精確度、雙精確度和1、2、4或8位元組整數值的128位向量進行計算。 也加入了雙精確度純量指示。

- **AVX**引進了向量和浮點純量指示的替代指令編碼，可允許128位或256位的向量，而零則會將所有向量結果擴充為完整的向量大小。 （如需舊版相容性，SSE 樣式向量指令會保留超過位127的所有位）。大部分的浮點運算會擴充至256位。

- **AVX2**會將大部分的整數作業延伸至256位向量，並可使用已融合的乘法-ADD （FMA）指示。

- **AVX512**引進了另一個允許512位向量的指令編碼形式，加上一些其他選擇性功能。 此外，也會新增其他作業的指示。

優化工具會根據指定的 **/arch** ，選擇使用向量指示的時機和方式。 純量浮點計算會使用 SSE 或 AVX 指令來執行（如果有的話）。 某些呼叫慣例會指定在 x87 堆疊上傳遞浮點引數，因此，您的程式碼可以混合使用 x87 和 SSE/AVX 指令來進行浮點計算。 整數向量指令也可以用於某些64位整數作業（如果有的話）。

除了向量和浮點純量指令以外，每個 **/arch**選項也可能會啟用與該選項相關聯之其他非向量指令的使用。 例如，CMOVcc 指令系列第一次出現在 Intel Pentium Pro 處理器上。 由於 SSE 指示是在後續的 Intel Pentium III 處理器中引進，因此可能會產生 CMOVcc 指示，除非指定了 **/arch： IA32** 。

在 x87 程式碼中，浮點運算通常會四捨五入為雙精確度（64位），但您可以使用 `_controlfp` 來修改 FP 控制字組，包括將有效位數控制項設定為擴充精確度（80位）或單精確度（32位）。 如需詳細資訊，請參閱 [_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。 SSE 和 AVX 對於每個作業都有個別的單精確度和雙精確度的指示，因此 SSE/AVX 程式碼沒有對等的對應。 這可能會變更當浮點運算的結果直接用於進一步的計算，而不是將它指派給使用者變數時，結果的舍入方式。 請考慮下列事項：

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

使用明確指派：

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/arch**和[/QIfist](qifist-suppress-ftol.md)不能用在相同的編譯模組上。 **/QIfist**選項會將浮點的舍入行為變更為整數轉換。 預設行為是截斷（向零舍入），而 **/QIfist**選項指定使用浮點環境舍入模式。 因為這會變更所有浮點到整數轉換的行為，所以此旗標已被取代。 針對 SSE 或 AVX 進行編譯時，您可以使用內建函式順序，將浮點值舍入為整數，方法是使用浮點環境進位模式：

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

`_M_IX86_FP`、`__AVX__`、`__AVX2__`、`__AVX512F__`、`__AVX512CD__`、`__AVX512BW__`、`__AVX512DQ__` 和 `__AVX512VL__` 宏會指出使用了哪個 **/arch**編譯器選項（如果有的話）。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch： AVX2**選項和 `__AVX2__` 宏是在 Visual Studio 2013 Update 2，版本12.0.34567.1 中引進。 有限的 **/arch 支援： AVX512**已在 Visual Studio 2017 中新增，並在 Visual Studio 2019 中展開。

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>若要在 Visual Studio 中為 AVX、AVX2、AVX512、IA32、SSE 或 SSE2 設定此編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定]**屬性**[ **CC++ /** 資料夾]。

1. 選取 [程式**代碼產生**] 屬性頁。

1. 修改 [**啟用增強的指令集**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>另請參閱

[/arch (最小 CPU 架構)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
