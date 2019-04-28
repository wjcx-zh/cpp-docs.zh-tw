---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: c515307ee3a49ef746eea939e90d7aecbd661b95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295278"
---
# <a name="arch-x64"></a>/arch (x64)

在 x64 上，為程式碼產生指定架構。 另請參閱[/arch (x86)](arch-x86.md)並[/arch (ARM)](arch-arm.md)。

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

**/arch**只會影響程式碼產生原生函式。 當您使用[/clr](clr-common-language-runtime-compilation.md)進行編譯， **/arch**不有 managed 函式的程式碼產生任何影響。

`__AVX__`前置處理器符號會定義當 **/arch: avx**指定編譯器選項。 `__AVX2__`前置處理器符號會定義當 **/arch:avx2**指定編譯器選項。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。 **/Arch:avx2**選項已引入 Visual Studio 2013 Update 2 12.0.34567.1 版。

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定 /arch:AVX 或 /arch:AVX2 編譯器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性**， **C /C++** 資料夾。

1. 選取 **程式碼產生**屬性頁。

1. 在 **啟用進階指令集**下拉式清單方塊中，選擇**Advanced Vector Extensions (/ /arch: AVX)** 或是**Advanced Vector Extensions 2 (/ arch:avx2)**。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>另請參閱

[/arch (最小 CPU 架構)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
