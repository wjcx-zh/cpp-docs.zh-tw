---
title: /X (忽略標準 Include 路徑)
ms.date: 11/04/2016
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 23942803ae0a25aaddd7f5844b303528c2c7ccb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663758"
---
# <a name="x-ignore-standard-include-paths"></a>/X (忽略標準 Include 路徑)

防止編譯器搜尋 include 檔中的 PATH 和 INCLUDE 環境變數所指定的目錄中。

## <a name="syntax"></a>語法

```
/X
```

## <a name="remarks"></a>備註

您可以使用這個選項搭配[/I （其他 Include 目錄）](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) 選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **前置處理器**屬性頁。

1. 修改**忽略標準 Include 路徑**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。

## <a name="example"></a>範例

在下列命令中，`/X`會告訴編譯器忽略在 PATH 和 INCLUDE 環境變數所指定的位置和`/I`指定目錄中用來尋找 include 檔：

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)