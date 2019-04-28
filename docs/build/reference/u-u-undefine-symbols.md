---
title: /U、/u (取消定義符號)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: bfc03ebd5c900bf8bf81b4a50eed02111baf85ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316999"
---
# <a name="u-u-undefine-symbols"></a>/U、/u (取消定義符號)

**/U**編譯器選項會取消指定的前置處理器符號的定義。 **/U**編譯器選項取消定義編譯器所定義的 Microsoft 特定符號。

## <a name="syntax"></a>語法

```
/U[ ]symbol
/u
```

## <a name="arguments"></a>引數

*symbol*<br/>
若要取消定義前置處理器符號。

## <a name="remarks"></a>備註

既不 **/U**或 **/u**選項可以取消建立所使用的符號 **#define**指示詞。

**/U**選項可以取消使用先前定義的符號 **/D**選項。

根據預設，編譯器會定義下列的 Microsoft 特定符號。

|符號|功能|
|------------|--------------|
|_CHAR_UNSIGNED|預設 char 類型不帶正負號。 定義何時[/J](j-default-char-type-is-unsigned.md)指定選項。|
|_CPPRTTI|針對以編譯程式碼定義[/GR](gr-enable-run-time-type-information.md)選項。|
|_CPPUNWIND|針對以編譯程式碼定義[/EHsc](eh-exception-handling-model.md)選項。|
|_DLL|定義何時[/MD](md-mt-ld-use-run-time-library.md)指定選項。|
|_M_IX86|根據預設，定義為 600，適用於 x86 的目標。|
|_MSC_VER|如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。|
|_WIN32|定義 WIN32 應用程式。 永遠會定義。|
|_MT|定義何時[/MD 或 /MT](md-mt-ld-use-run-time-library.md)指定選項。|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 [C/C++]  資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**取消定義前置處理器定義**或是**取消所有前置處理器定義**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A>或 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)<br/>
[/J (預設 char 類型為 unsigned)](j-default-char-type-is-unsigned.md)<br/>
[/GR (啟用執行階段類型資訊)](gr-enable-run-time-type-information.md)<br/>
[/EH (例外狀況處理模型)](eh-exception-handling-model.md)<br/>
[/MD、/MT、/LD (使用執行階段程式庫)](md-mt-ld-use-run-time-library.md)
