---
title: /analyze (程式碼分析)
ms.date: 04/26/2018
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
ms.openlocfilehash: 057fabe9612f84af07649d7a4f7bbf6d83e01f6c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426208"
---
# <a name="analyze-code-analysis"></a>/analyze (程式碼分析)

啟用程式碼分析和控制選項。

## <a name="syntax"></a>語法

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>引數

/ 分析會在分析中的預設模式。 分析會輸出至**輸出**等其他錯誤訊息的視窗。 使用 **/ 分析-** 來明確關閉分析。

/analyze: WX-指定 **/analyze: WX-** 程式碼分析警告的方法不要視為錯誤當您使用編譯 **/WX**。 如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../../build/reference/compiler-option-warning-level.md)。

/analyze: log`filename`詳細的分析器結果會寫入為 XML 檔案所指定`filename`。

/analyze: quiet 會關閉分析器的輸出**輸出**視窗。

/analyze: stacksize `number` `number`會搭配這個選項的參數指定的大小，以位元組為單位的警告之堆疊框架[C6262](/visualstudio/code-quality/c6262)產生。 如果未指定這個參數，則預設的堆疊框架大小為 16KB。

/analyze: max_paths `number` `number`會搭配這個選項的參數會指定要分析的程式碼路徑的最大數目。 如果未指定這個參數，則預設數目為 256。 值越大，執行的檢查就越徹底，但是也可能需要較長的時間進行分析。

/analyze： 只一般而言，編譯器會產生程式碼，進行更多語法檢查之後執行分析器。 **/Analyze： 只有**選項會關閉這個程式碼產生階段; 這可讓分析加快，但不是會發出編譯錯誤和可能已由編譯器的程式碼產生階段探索到的警告。 如果程式並不是沒有程式碼產生錯誤，分析結果可能就不可靠，因此，建議您只有在程式碼已通過程式碼產生語法檢查且沒有錯誤的情況下，才使用這個選項。

/analyze: ruleset`<file_path>.ruleset`可讓您指定的規則集來分析，包括您可以建立自己的自訂規則集。 當設定這個參數時，因為它會排除指定的規則集執行前的非成員的規則引擎會更有效率。 當未設定此參數，則引擎會檢查所有規則。

隨附於 Visual Studio 的 ruleset 位於 **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule 集。**

下列範例自訂規則集會告訴規則引擎，以檢查 C6001 和 C26494。 您可以將此檔案，任何地方，只要它有`.ruleset`延伸模組，並提供引數中的完整路徑。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/analyze： 外掛程式可讓指定的 PREfast 外掛程式程式碼分析的一部分執行。
LocalEspC.dll 是外掛程式實作並行存取相關的程式碼分析簽入範圍的 C261XX 警告。 例如， [C26100](/visualstudio/code-quality/c26100)， [C26101](/visualstudio/code-quality/c26101)，...， [C26167](/visualstudio/code-quality/c26167)。

若要執行 LocalEspC.dll，使用這個編譯器選項： **/analyze： 外掛程式 LocalEspC.dll**

若要執行 CppCoreCheck.dll，第一次在開發人員命令提示字元執行此命令：

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

然後使用這個編譯器選項： **/analyze： 外掛程式 EspXEngine.dll**。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 程式碼分析 C/c + + 概觀](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)並[程式碼分析 C/c + + 警告](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**程式碼分析**節點。

1. 選取 [ **一般** ] 屬性頁。

1. 修改一或多個**程式碼分析**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。

## <a name="see-also"></a>另請參閱

- [編譯器選項](../../build/reference/compiler-options.md)
- [設定編譯器選項](../../build/reference/setting-compiler-options.md)
