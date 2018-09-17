---
title: -I (其他 Include 目錄) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs:
- C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a580488650a1272ec1dffcd1f0ba27c736df92da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705337"
---
# <a name="i-additional-include-directories"></a>/I (其他 Include 目錄)

將目錄加入至搜尋 include 檔的目錄清單。

## <a name="syntax"></a>語法

```
/I[ ]directory
```

## <a name="arguments"></a>引數

*目錄*<br/>
要加入的目錄清單中的目錄中搜尋 include 檔。

## <a name="remarks"></a>備註

若要新增多個目錄，請多次使用此選項。 找到指定的 include 檔時，才會搜尋目錄。

您可以使用此選項，以忽略標準 Include 路徑 ([/X （忽略標準 Include 路徑）](../../build/reference/x-ignore-standard-include-paths.md)) 選項。

編譯器會搜尋目錄以下列順序：

1. 包含原始程式檔的目錄。

1. 使用指定的目錄 **/I**選項，CL 遇到它們的順序。

1. 中指定的目錄**INCLUDE**環境變數。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 [C/C++]  資料夾。

1. 按一下 **一般**屬性頁。

1. 修改**其他 Include 目錄**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。

## <a name="example"></a>範例

下列命令會尋找 MAIN.c 要求依下列順序的 include 檔案： 包含 MAIN.c，然後在 [\INCLUDE] 目錄中，然後在 \MY\INCLUDE 目錄中，且最後的目錄中指派給包含的目錄中的第一個環境變數。

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)