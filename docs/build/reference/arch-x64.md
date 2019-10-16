---
title: /arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 0ade6d9f744339ebaf38981d81334340b56080cb
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816230"
---
# <a name="arch-x64"></a>/arch (x64)

在 x64 上，為程式碼產生指定架構。 另請參閱[/arch （x86）](arch-x86.md)和[/arch （ARM）](arch-arm.md)。

## <a name="syntax"></a>語法

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>引數

**/arch:AVX**<br/>
啟用 Intel Advanced Vector Extensions 指令的使用。

**/arch:AVX2**<br/>
啟用 Intel Advanced Vector Extensions 2 指令的使用。

**/arch： AVX512**<br/>
啟用 Intel Advanced Vector Extensions 512 指示的使用。

## <a name="remarks"></a>備註

**/Arch**選項可讓您使用特定的指令集延伸模組，特別是針對向量計算，適用于 INTEL 和 AMD 的處理器。 一般來說，最新引進的處理器可能支援較舊處理器支援的額外延伸模組，但您應該參閱特定處理器的檔，或使用 __ 測試指令集延伸模組支援使用指令集延伸模組執行程式碼之前的 [cpuid](../../intrinsics/cpuid-cpuidex.md)。

**/arch**只會影響原生函式的程式碼產生。 當您使用[/clr](clr-common-language-runtime-compilation.md)進行編譯時， **/arch**不會影響 managed 函式的程式碼產生。

處理器擴充功能具有下列特性：

- 預設模式會使用 SSE2 指示來進行純量浮點和向量計算。 這些指示允許以單精確度、雙精確度和1、2、4或8位元組整數值的128位向量計算，以及單精確度和雙精確度純量浮點值。

- **AVX**引進了向量和浮點純量指示的替代指令編碼，可允許128位或256位的向量，而零則會將所有向量結果擴充為完整的向量大小。 （如需舊版相容性，SSE 樣式向量指令會保留超過位127的所有位）。大部分的浮點運算會擴充至256位。

- **AVX2**會將大部分的整數作業延伸至256位向量，並允許使用已融合的乘法-ADD （FMA）指示。

- **AVX-512**引進了另一個允許512位向量的指令編碼形式，加上一些其他選擇性功能。 此外，也會新增其他作業的指示。

每個 **/arch**選項也可能會啟用與該選項相關聯的其他非向量指示的使用。 例如，當指定了 **/arch： AVX2**時，會使用特定的 BMI 指令。

指定 **/arch： AVX**、 **/arch： AVX2**或 **/arch： AVX512**編譯器選項時，會定義 `__AVX__` 預處理器符號。 指定 **/arch： AVX2**或 **/arch： AVX512**編譯器選項時，會定義 `__AVX2__` 預處理器符號。 當指定 **/arch： AVX512**編譯器選項時，會定義 `__AVX512F__`、`__AVX512CD__`、`__AVX512BW__`、`__AVX512DQ__` 和 @no__t 4 預處理器符號。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch： AVX2**選項是在 Visual Studio 2013 Update 2，版本12.0.34567.1 中引進。 有限的 **/arch 支援： AVX512**已在 Visual Studio 2017 中新增，並在 Visual Studio 2019 中展開。

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定/arch： AVX、/arch： AVX2 或/arch： AVX512 編譯器選項

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定]**屬性**[ **CC++ /** 資料夾]。

1. 選取 [程式**代碼產生**] 屬性頁。

1. 在 [**啟用增強的指令集**] 下拉式方塊中，選擇 [ **Advanced vector extensions （/arch： AVX）** ]、[ **advanced vector EXTENSIONS 2 （/arch： AVX2）** ] 或 [ **ADVANCED vector extensions 512 （/arch： AVX512）** ]。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>另請參閱

[/arch (最小 CPU 架構)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
