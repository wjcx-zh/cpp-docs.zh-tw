---
title: /Za、/Ze (停用語言擴充功能)
ms.date: 02/19/2019
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
ms.openlocfilehash: 9a2584591f6ca22d6767a5c447ffb72bea0a78ea
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825871"
---
# <a name="za-ze-disable-language-extensions"></a>/Za、/Ze (停用語言擴充功能)

**/Za**編譯器選項會停用併發出與 ANSI C89/ISO C90 不相容之 Microsoft Extensions to C 的錯誤。 已淘汰的 **/ze**編譯器選項可啟用 Microsoft 擴充功能。 Microsoft 擴充功能預設為啟用。

## <a name="syntax"></a>語法

> **/Za**\
> **/Ze**

## <a name="remarks"></a>備註

> [!NOTE]
> 不建議將程式碼編譯為 c + + 時使用 **/za** 。 **/Ze**選項已被取代，因為它的行為預設是開啟的。 如需已被取代的編譯器選項清單，請參閱[已取代和已移除的編譯器選項](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)。

Microsoft C/c + + 編譯器支援 C 程式碼的編譯，方法有兩種：

- 當原始程式檔的副檔名為 *.c* ，或指定了[/tc](tc-tp-tc-tp-specify-source-file-type.md)或[/tc](tc-tp-tc-tp-specify-source-file-type.md)選項時，編譯器預設會使用 c 編譯模式。 C 編譯器是 C89/C90 編譯器，預設會啟用 C 語言的 Microsoft 擴充功能。 如需特定延伸模組的詳細資訊，請參閱[Microsoft extensions To c And c + +](microsoft-extensions-to-c-and-cpp.md)。 當同時指定 C 編譯和 **/za**選項時，c 編譯器會嚴格符合 C89/C90 標準。 編譯器會將 Microsoft 擴充的關鍵字視為簡單的識別碼，停用其他 microsoft 擴充功能，並自動為 C 程式定義[ \_ \_STDC\_ ](../../preprocessor/predefined-macros.md)預先定義宏。

- 編譯器可以在 c + + 編譯模式中編譯 C 程式碼。 此行為是原始程式檔的預設值，但在指定了[/tp](tc-tp-tc-tp-specify-source-file-type.md)或[/tp](tc-tp-tc-tp-specify-source-file-type.md)選項時，不具有 *.c 副檔名。* 在 c + + 編譯模式中，編譯器支援已併入 c + + 標準中的 ISO C99 和 C11 標準部分。 幾乎所有 C 程式碼也都是有效的 c + + 程式碼。 少數 C 關鍵字和程式碼結構不是有效的 c + + 程式碼，或在 c + + 中以不同方式加以解讀。 在這些情況下，編譯器會根據 c + + 標準來運作。 在 c + + 編譯模式中， **/za**選項可能會造成非預期的行為，因此不建議使用。

其他編譯器選項可能會影響編譯器確保標準一致性的方式。 如需指定特定標準 C 和 c + + 行為設定的方式，請參閱[/zc](zc-conformance.md)編譯器選項。 如需其他 c + + 標準一致性設定，請參閱[/permissive-](permissive-standards-conformance.md)和[/std](std-specify-language-standard-version.md)編譯器選項。

如需 Visual C++ 之一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在流覽窗格中，選擇 [設定] [**屬性** > ] [**c/c + +** > **語言**]。

1. 修改 [**停用語言擴充**功能] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>＞。

## <a name="see-also"></a>請參閱

[編譯器選項](compiler-options.md)<br/>
[/Zc (一致性)](zc-conformance.md)<br/>
[/permissive- (標準一致性)](permissive-standards-conformance.md)<br/>
[/std （指定語言標準版本）](std-specify-language-standard-version.md)<br/>
