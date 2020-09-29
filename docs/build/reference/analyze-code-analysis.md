---
title: /analyze (程式碼分析)
description: Microsoft c + + 編譯器/analyze 選項語法和用法。
ms.date: 07/27/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: e970872e89132aed52190b8688f2cdaccab5ea6f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500086"
---
# <a name="analyze-code-analysis"></a>`/analyze` (程式碼分析) 

啟用程式碼分析和控制選項。

## <a name="syntax"></a>Syntax

::: moniker range=">=vs-2017"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***延伸*模組\
> **`/analyze:log`***檔案名*\
> **`/analyze:max_paths`***數位*\
> **`/analyze:only`**\
> **`/analyze:plugin`***外掛程式-dll*\
> **`/analyze:quiet`**\
> **`/analyze:ruleset`***規則集*\
> **`/analyze:stacksize`***數位*\
> **`/analyze:WX-`**

::: moniker-end
::: moniker range="vs-2015"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***延伸*模組\
> **`/analyze:log`***檔案名*\
> **`/analyze:max_paths`***數位*\
> **`/analyze:only`**\
> **`/analyze:plugin`***外掛程式-dll*\
> **`/analyze:quiet`**\
> **`/analyze:stacksize`***數位*\
> **`/analyze:WX-`**

::: moniker-end

## <a name="arguments"></a>引數

**`/analyze`**\
以預設模式開啟分析。 分析輸出會移至主控台或 Visual Studio **輸出** 視窗，如同其他錯誤訊息。 使用 **`/analyze-`** 以明確關閉分析。

**`/analyze:autolog`**\
詳細的分析器結果會以 XML 的形式寫入到與原始程式檔相同的基底名稱，以及的副檔名 *`.pftlog`* 。 **`/analyze:autolog-`** 停用此記錄檔。

**`/analyze:autolog:ext`***延伸*模組\
詳細的分析器結果會以 XML 的形式寫入到與原始程式檔相同的基底名稱*和延伸模組的副檔名。*

**`/analyze:log`***檔案名*\
詳細的分析器結果會以 XML 的形式寫入至 *檔案名*所指定的檔案。

**`/analyze:max_paths`***數位*\
搭配這個選項使用的 *數位* 參數會指定要分析的程式碼路徑數目上限。 如果未指定此參數，則預設值為256。 較大的值會造成更完整的檢查，但分析可能需要較長的時間。

**`/analyze:only`**\
通常，編譯器在執行分析器之後，會產生程式碼並進行更多語法檢查。 **`/analyze:only`** 此選項會關閉此程式碼產生階段。 它讓分析更快，但不會發出編譯器的程式碼產生階段可能找到的編譯器錯誤和警告。 如果程式不是程式碼產生的錯誤，則分析結果可能不可靠。 建議您只有在程式碼已通過程式碼產生語法檢查而沒有錯誤時，才使用此選項。

**`/analyze:plugin`***外掛程式-dll*\
啟用指定的 PREfast 外掛程式作為程式碼分析執行的一部分。

::: moniker range="<=vs-2017"

LocalEspC.dll 是在 C261XX 警告範圍中執行並行相關程式碼分析檢查的外掛程式。 例如， [C26100](../../code-quality/c26100.md)、 [C26101](../../code-quality/c26101.md)、...、  [C26167](../../code-quality/c26167.md)。

若要執行 LocalEspC.dll，請使用這個編譯器選項： **`/analyze:plugin LocalEspC.dll`**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck.dll 會在 C261XX 警告的範圍內實行並行相關的程式碼分析檢查。 例如， [C26100](../../code-quality/c26100.md)、 [C26101](../../code-quality/c26101.md)、...、  [C26167](../../code-quality/c26167.md)。

若要執行 ConcurrencyCheck.dll，請先從開發人員命令提示字元執行下列命令：

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

然後使用此編譯器選項： **`/analyze:plugin EspXEngine.dll`** 。

若要執行 CppCoreCheck.dll，請先從開發人員命令提示字元執行下列命令：

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

然後使用此編譯器選項： **`/analyze:plugin EspXEngine.dll`** 。

::: moniker-end

**`/analyze:quiet`**\
關閉主控台或 Visual Studio **輸出** 視窗的分析器輸出。

::: moniker range=">=vs-2017"

**`/analyze:ruleset`***file_path 規則集*\
可讓您指定要分析的規則集，包括您可以自行建立的自訂規則集。 設定此參數時，規則引擎會更有效率，因為它會在執行之前排除指定之規則集的非成員。 否則，引擎會檢查所有規則。

在中可以找到 Visual Studio 隨附的規則集 *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* 。

下列自訂規則集範例會告知規則引擎檢查 C6001 和 C26494。 您可以將這個檔案放在任何位置，只要它具有 *`.ruleset`* 副檔名，就可以在引數中提供完整路徑。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

**`/analyze:stacksize`***數位*\
搭配這個選項使用的 *數位* 參數會指定產生警告 [C6262](../../code-quality/c6262.md) 之堆疊框架的大小（以位元組為單位）。 *Number*之前的空格是選擇性的。 如果未指定此參數，預設會16KB 堆疊框架大小。

**`/analyze:WX-`**\
當您使用編譯時，不會將程式碼分析警告視為錯誤 **`/WX`** 。 如需詳細資訊，請參閱[ `/WX` (警告層級) ](compiler-option-warning-level.md)。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 C/c [+ + 的程式碼分析總覽](../../code-quality/code-analysis-for-c-cpp-overview.md) 和 [c/c + + 警告的程式碼分析](../../code-quality/code-analysis-for-c-cpp-warnings.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**程式  >  **代碼分析**  >  **一般**] 屬性頁。

1. 修改一個或多個程式 **代碼分析** 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
