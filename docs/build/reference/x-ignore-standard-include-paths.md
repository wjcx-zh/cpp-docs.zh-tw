---
title: /X (忽略標準 Include 路徑)
ms.date: 07/18/2019
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 16f903b98d69472fe1a33b084fe6393ecf9ec001
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341048"
---
# <a name="x-ignore-standard-include-paths"></a>/X (忽略標準 Include 路徑)

防止編譯器在 PATH 和 INCLUDE 環境變數所指定的目錄中搜尋 include 檔案。

## <a name="syntax"></a>語法

```
/X
```

## <a name="remarks"></a>備註

您可以使用此選項搭配[/i (其他 Include 目錄)](i-additional-include-directories.md) ( **/i** `directory`) 選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 [**預處理器**] 屬性頁。

1. 修改 [**忽略標準 Include 路徑**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。

## <a name="example"></a>範例

在下列命令中, `/X`會告知編譯器忽略 PATH 所指定的位置並包含環境變數, 並`/I`指定要在其中尋找 INCLUDE 檔案的目錄:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
