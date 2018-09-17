---
title: -showIncludes （列示包含檔） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
dev_langs:
- C++
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51305212f97482c6963ee2ba0d272c5c4692416e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709383"
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