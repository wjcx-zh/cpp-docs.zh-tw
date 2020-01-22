---
title: /QIntel-jcc-erratum
description: 描述 Microsoft C/C++編譯器（MSVC）/QIntel-jcc-erratum 選項。
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520876"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

Visual Studio 2019 16.5 版和更新版本中提供 **/QIntel-jcc-erratum**選項。

::: moniker-end

::: moniker range=">=vs-2019"

指定編譯器會產生指示，以降低特定 Intel 處理器中 Intel 跳躍條件程式碼（JCC）錯誤代碼微碼更新所造成的效能影響。

## <a name="syntax"></a>語法

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>備註

在 **/QIntel-jcc-erratum**下，編譯器會偵測在32位元組界限上交叉或結束的跳躍和以宏為融合的跳躍指示。 它會將這些指示與界限對齊。 這項變更可降低微碼更新的效能影響，以防止特定 Intel 處理器發生 JCC 錯誤。 如需錯誤的詳細資訊，請參閱 Intel 網站上[跳躍條件程式碼錯誤](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf)的緩和措施。

Visual Studio 2019 16.5 版和更新版本中提供 **/QIntel-jcc-erratum**選項。 此選項只適用于以 x86 和 x64 為目標的編譯器。 以 ARM 處理器為目標的編譯器中無法使用此選項。

**/QIntel-jcc-erratum**選項預設為關閉，而且僅適用于優化的組建。 此選項可能會增加程式碼大小。

**/QIntel-jcc-erratum**與[/clr](clr-common-language-runtime-compilation.md)不相容。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在 [ **C/C++**  > 程式**代碼產生**] 屬性頁中選取 [設定**屬性**] >。

1. 選取 [**啟用 INTEL JCC 錯誤] 緩和**屬性的值。 選擇 [確定] 以套用變更。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>請參閱

[/Q 選項（低層級作業）](q-options-low-level-operations.md)\
[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)

::: moniker-end
