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
ms.openlocfilehash: 0c968f406043f5c0b5fd04c18e22a77cd640d873
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424154"
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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**顯示包含**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
