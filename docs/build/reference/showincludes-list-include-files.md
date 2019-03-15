---
title: /showIncludes (列示包含檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
ms.openlocfilehash: d454054c132976a899fcc4a56a63be427e79beec
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819230"
---
# <a name="showincludes-list-include-files"></a>/showIncludes (列示包含檔)

可讓編譯器輸出 include 檔案的清單。 巢狀包含的檔案也是顯示 （檔案所包含的您所包含的檔案）。

## <a name="syntax"></a>語法

```
/showIncludes
```

## <a name="remarks"></a>備註

在編譯期間遇到 include 檔時，會輸出訊息，例如：

```
Note: including file: d:\MyDir\include\stdio.h
```

巢狀包含的檔案會以縮排，而每個層級的巢狀結構、 一個空格，例如：

```
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

在此情況下，`2.h`包含從`1.h`，因此縮排。

**/ShowIncludes**選項會發出至`stderr`，而非`stdout`。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**顯示包含**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
