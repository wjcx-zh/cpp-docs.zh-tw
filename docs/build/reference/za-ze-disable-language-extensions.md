---
title: /Za、/Ze (停用語言擴充功能)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: a3d25f71739f9948f2c0237efbaeaf8fa89f2114
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549717"
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze (停用語言擴充功能)

**/Za**編譯器選項會發出與 ANSI C89 或 ISO C + + 11 不相容的語言建構的錯誤。 **/Ze**編譯器選項，預設為開啟，啟用 Microsoft 擴充功能。

## <a name="syntax"></a>語法

```
/Za
/Ze
```

## <a name="remarks"></a>備註

> [!NOTE]
>  **/Ze**選項已被取代，因為它的行為預設為開啟。 我們建議您改用[/Zc （一致性）](../../build/reference/zc-conformance.md)編譯器選項，以控制特定的語言擴充功能。 如需已被取代的編譯器選項的清單，請參閱 <<c0>  **已取代及移除的編譯器選項**一節[依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)。

Visual c + + 編譯器提供多種功能，在 ANSI C89、 ISO C99 或 ISO c + + 標準中所指定之外。 這些功能統稱為 Microsoft 擴充功能對 C 和 c + +。 這些擴充功能可供使用的預設值，且無法使用時 **/Za**指定選項。 如需特定的擴充功能的詳細資訊，請參閱[對 C 和 c + + 的 Microsoft 擴充功能](../../build/reference/microsoft-extensions-to-c-and-cpp.md)。

我們建議您停用語言擴充功能藉由指定 **/Za**選項，如果您打算移植程式至其他環境。 當 **/Za**指定，則編譯器會將 Microsoft 擴充關鍵字做為簡單識別項，會停用其他的 Microsoft 擴充功能，並會自動定義`__STDC__`C 程式的預先定義巨集。

搭配使用其他編譯器選項 **/Za**可能會影響編譯器確保符合標準的方式。

如需指定特定的標準行為的設定方式，請參閱[/Zc](../../build/reference/zc-conformance.md)編譯器選項。

如需 Visual c + + 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 在 [導覽] 窗格中，選擇**組態屬性**， **C/c + +**，**語言**。

1. 修改**停用語言擴充功能**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (一致性)](../../build/reference/zc-conformance.md)
