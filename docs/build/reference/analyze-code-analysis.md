---
title: -分析 （程式碼分析） |Microsoft 文件
ms.custom: ''
ms.date: 04/26/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f706c3ff32635384766ac2c028cc0e5096118b8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="analyze-code-analysis"></a>/analyze (程式碼分析)

啟用程式碼分析和控制選項。

## <a name="syntax"></a>語法

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>引數

 /analyze  
 以預設模式開啟分析。 分析會輸出至**輸出**視窗，就像其他錯誤訊息一樣。 使用 **/ 分析-** 明確關閉分析。

 /analyze:WX-  
 指定 **/analyze: WX-** 程式碼分析警告，表示不要視為錯誤當您使用編譯 **/WX**。 如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../../build/reference/compiler-option-warning-level.md)。

 /analyze:log `filename`  
 詳細的分析器結果會做為 XML 寫入至 `filename` 所指定的檔案。

 /analyze:quiet  
 關閉 分析器輸出至**輸出**視窗。

 /analyze:stacksize `number`  
 `number`參數會搭配這個選項使用指定大小，以位元組為單位的警告之堆疊框架[C6262](/visualstudio/code-quality/c6262)產生。 如果未指定這個參數，則預設的堆疊框架大小為 16KB。

 /analyze:max_paths `number`  
 搭配這個選項使用的 `number` 參數會指定要分析的程式碼路徑數目上限。 如果未指定這個參數，則預設數目為 256。 值越大，執行的檢查就越徹底，但是也可能需要較長的時間進行分析。

 /analyze:only  
 通常，編譯器在執行分析器之後，會產生程式碼並進行更多語法檢查。 **/Analyze： 只有**選項會關閉這個程式碼產生階段; 這可讓分析加快，但不是會產生編譯錯誤和可能已探索的編譯器的程式碼產生階段的警告。 如果程式並不是沒有程式碼產生錯誤，分析結果可能就不可靠，因此，建議您只有在程式碼已通過程式碼產生語法檢查且沒有錯誤的情況下，才使用這個選項。

 /analyze： 規則集 `<file_path>.ruleset`  
可讓您指定的規則集若要分析，包括您可以建立自己的自訂規則集。 當設定這個參數時，因為它會排除指定的規則集執行前的非成員的規則引擎會更有效率。 當未設定此參數時，則引擎會檢查所有規則。

隨附於 Visual Studio 的 ruleset 存在於 **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets。**

下列範例自訂規則集會告知 「 規則引擎，以檢查 C6001 和 C26494。 您可以將此檔案，任何位置，只要它有`.ruleset`延伸模組，並提供引數中的完整路徑。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/analyze: plugin  
當程式碼分析的一部分執行時，可讓指定 PREfast 外掛程式。 LocalEspC.dll 是外掛程式實作並行存取相關的程式碼分析簽入範圍的 C261XX 警告。 例如， [C26100](/visualstudio/code-quality/c26100)， [C26101](/visualstudio/code-quality/c26101)，...， [C26167](/visualstudio/code-quality/c26167)。

若要執行 LocalEspC.dll，使用這個編譯器選項： **/analyze: plugin LocalEspC.dll**

若要執行 CppCoreCheck.dll，第一次從開發人員命令提示字元執行此命令：

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

然後使用這個編譯器選項： **/analyze: plugin EspXEngine.dll**。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[程式碼分析 C/c + + 概觀](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)和[程式碼分析 C/c + + 警告](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開**組態屬性**節點。

1. 展開**程式碼分析**節點。

1. 選取 [ **一般** ] 屬性頁。

1. 修改一或多個**程式碼分析**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。

## <a name="see-also"></a>另請參閱

- [編譯器選項](../../build/reference/compiler-options.md)
- [設定編譯器選項](../../build/reference/setting-compiler-options.md)