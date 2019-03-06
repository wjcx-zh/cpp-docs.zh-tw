---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: ac34a18efbf31787889cc4fe31ebd3d8473df0eb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421853"
---
# <a name="arch-x64"></a>/arch (x64)

在 x64 上，為程式碼產生指定架構。 另請參閱[/arch (x86)](../../build/reference/arch-x86.md)並[/arch (ARM)](../../build/reference/arch-arm.md)。

## <a name="syntax"></a>語法

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>引數

**/arch:AVX**<br/>
啟用 Intel Advanced Vector Extensions 指令的使用。

**/arch:AVX2**<br/>
啟用 Intel Advanced Vector Extensions 2 指令的使用。

## <a name="remarks"></a>備註

**/arch**只會影響程式碼產生原生函式。 當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)進行編譯， **/arch**不有 managed 函式的程式碼產生任何影響。

`__AVX__`前置處理器符號會定義當 **/arch: avx**指定編譯器選項。 `__AVX2__`前置處理器符號會定義當 **/arch:avx2**指定編譯器選項。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch:avx2**選項已引入 Visual Studio 2013 Update 2 12.0.34567.1 版。

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定 /arch:AVX 或 /arch:AVX2 編譯器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性**， **C/c + +** 資料夾。

1. 選取 **程式碼產生**屬性頁。

1. 在 **啟用進階指令集**下拉式清單方塊中，選擇**Advanced Vector Extensions (/ /arch: AVX)** 或是**Advanced Vector Extensions 2 (/ arch:avx2)**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>另請參閱

[/arch (最小 CPU 架構)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
