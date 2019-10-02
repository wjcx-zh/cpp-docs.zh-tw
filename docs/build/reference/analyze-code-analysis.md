---
title: /analyze (程式碼分析)
ms.date: 10/01/2019
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
ms.openlocfilehash: d647045d76dc32544f8146424b220547890b0943
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816326"
---
# <a name="analyze-code-analysis"></a>/analyze (程式碼分析)

啟用程式碼分析和控制選項。

## <a name="syntax"></a>語法

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>引數

/analyze 會以預設模式開啟分析。 分析輸出會移至 [**輸出**] 視窗，就像其他錯誤訊息一樣。 使用 **/analyze-** 明確關閉分析。

/analyze： WX-指定 **/analyze： WX-** 表示當您使用 **/wx**進行編譯時，不會將程式碼分析警告視為錯誤。 如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](compiler-option-warning-level.md)。

/analyze： log `filename` 詳細的分析器結果會以 XML 的形式寫入至 `filename` 所指定的檔案。

/analyze： quiet 會關閉分析器輸出至 [**輸出**] 視窗。

/analyze： stacksize `number` 搭配此選項使用的 `number` 參數會指定產生警告[C6262](/visualstudio/code-quality/c6262)之堆疊框架的大小（以位元組為單位）。 @No__t-0 之前的空格是選擇性的。 如果未指定這個參數，則預設的堆疊框架大小為 16KB。

/analyze： max_paths `number` 搭配此選項使用的 `number` 參數指定要分析的程式碼路徑數目上限。 如果未指定這個參數，則預設數目為 256。 值越大，執行的檢查就越徹底，但是也可能需要較長的時間進行分析。

/analyze：只有編譯器會產生程式碼，並在執行分析器之後執行更多語法檢查。 **/Analyze： only**選項會關閉這個程式碼產生階段;這可加快分析速度，但不會發出編譯器的程式碼產生階段可能發現的編譯錯誤和警告。 如果程式並不是沒有程式碼產生錯誤，分析結果可能就不可靠，因此，建議您只有在程式碼已通過程式碼產生語法檢查且沒有錯誤的情況下，才使用這個選項。

/analyze：規則集 `<file_path>.ruleset` 可讓您指定要分析的規則集，包括您可以自行建立的自訂規則集。 設定此參數時，規則引擎會更有效率，因為它會在執行之前排除指定規則集的非成員。 未設定參數時，引擎會檢查所有規則。

Visual Studio 隨附的規則集可在 **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets**中找到。

下列範例自訂規則集會指示規則引擎檢查是否有 C6001 和 C26494。 您可以將此檔案放在任何位置，只要它具有 @no__t 0 的副檔名，並在引數中提供完整路徑。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/analyze：外掛程式會啟用指定的 PREfast 外掛程式，做為程式碼分析執行的一部分。
LocalEspC 是在 C261XX 警告範圍內，用來執行並行相關程式碼分析檢查的外掛程式。 例如， [C26100](/visualstudio/code-quality/c26100)、 [C26101](/visualstudio/code-quality/c26101)、...、 [C26167](/visualstudio/code-quality/c26167)。

若要執行 LocalEspC，請使用此編譯器選項： **/analyze：外掛程式 LocalEspC**

若要執行 CppCoreCheck，請先從開發人員命令提示字元執行此命令：

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

然後使用此編譯器選項： **/analyze：外掛程式 EspXEngine**。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[c/C++總覽的程式碼分析](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)和[c/C++警告的程式碼分析](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 展開 [程式**代碼分析**] 節點。

1. 選取 [ **一般** ] 屬性頁。

1. 修改一或多個程式**代碼分析**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 編譯器選項](compiler-options.md)
- [MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
