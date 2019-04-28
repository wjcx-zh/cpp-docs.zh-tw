---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: b732a74d5fe223fdaf3b161d4ae92093ab5df407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295198"
---
# <a name="arch-arm"></a>/arch (ARM)

為 ARM 上的程式碼產生指定架構。 另請參閱[/arch (x86)](arch-x86.md)並[/(x64)](arch-x64.md)。

## <a name="syntax"></a>語法

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>引數

**/arch:ARMv7VE**<br/>
啟用 ARMv7VE 虛擬擴充功能指令。

**/arch:VFPv4**<br/>
啟用 ARM VFPv4 指令。 如果未指定此選項，VFPv3 就是預設值。

## <a name="remarks"></a>備註

`_M_ARM_FP` （適用於僅 ARM) 的巨集指示何種，如果有的話 **/arch**編譯器選項使用。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。

當您使用[/clr](clr-common-language-runtime-compilation.md)進行編譯， **/arch**不有 managed 函式的程式碼產生任何影響。 **/arch**只會影響程式碼產生原生函式。

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /arch:ARMv7VE 或 /arch:VFPv4 編譯器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取  **C /C++** 資料夾。

1. 選取 **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入`/arch:ARMv7VE`或`/arch:VFPv4`。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>。

## <a name="see-also"></a>另請參閱

[/arch (最小 CPU 架構)](arch-minimum-cpu-architecture.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
