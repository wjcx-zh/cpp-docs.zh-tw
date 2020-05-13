---
title: /O1、/O2 (最小大小、最快速度)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: 3daf5dd5f9912194fd5d8aaeb4c7a312be142b69
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825337"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1、/O2 (最小大小、最快速度)

選取一組預先定義的選項，其會影響所產生程式碼的大小和速度。

## <a name="syntax"></a>語法

> O1
> /O2

## <a name="remarks"></a>備註

**/O1**和 **/O2**編譯器選項是一次設定數個特定優化選項的快速方式。 **/O1**選項會設定個別的優化選項，以在大部分案例中建立最小的程式碼。 **/O2**選項會設定在大部分案例中建立最快速程式碼的選項。 [發行組建] 的預設值為 [ **/O2** ] 選項。 下表顯示 **/O1**和 **/O2**所設定的特定選項：

|選項|相當於|
|------------|-------------------|
|**/O1** （最小大小）|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/gf](gf-eliminate-duplicate-strings.md) [/gy](gy-enable-function-level-linking.md)|
|**/O2** （最大化速度）|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/ot](os-ot-favor-small-code-favor-fast-code.md) [/oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/gf](gf-eliminate-duplicate-strings.md) [/gy](gy-enable-function-level-linking.md)|

**/O1**和 **/O2**是互斥的。

> [!NOTE]
> **x86 特定**\
> 這些選項表示使用框架指標省略（[/oy](oy-frame-pointer-omission.md)）選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在 [設定**屬性**] 下，開啟 [ **C/c + +** ]，然後選擇 [**優化**] 屬性頁。

1. 修改**優化**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>＞。

## <a name="see-also"></a>請參閱

[/O 選項 (最佳化程式碼)](o-options-optimize-code.md)<br/>
[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/EH (例外狀況處理模型)](eh-exception-handling-model.md)
