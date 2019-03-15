---
title: /I (其他 include 目錄)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: 6ec8b15e77fec5214013c484e617904ed29e8197
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807633"
---
# <a name="i-additional-include-directories"></a>/I (其他 include 目錄)

將目錄加入至搜尋 include 檔的目錄清單。

## <a name="syntax"></a>語法

> **/I**[ ]*directory*

### <a name="arguments"></a>引數

*directory*<br/>
要加入的目錄清單中的目錄中搜尋 include 檔。

## <a name="remarks"></a>備註

若要新增多個目錄，請多次使用此選項。 找到指定的 include 檔時，才會搜尋目錄。

您可以使用這個選項搭配 ([/X （忽略標準 Include 路徑）](x-ignore-standard-include-paths.md)) 選項。

編譯器會將目前目錄中搜尋以下列順序：

1. 如果使用指定[#include 指示詞](../../preprocessor/hash-include-directive-c-cpp.md)雙引號在表單中，會先搜尋本機目錄。 包含的檔案相同的目錄中開始搜尋 **#include**陳述式。 如果這無法找到檔案，它會搜尋在目前開啟的目錄包含檔案，它們已開啟的相反順序。 搜尋會從 Include 檔的父目錄開始，並向上繼續搜尋所有上層 Include 檔的目錄。

1. 如果使用指定 **#include**角中的指示詞括住的表單，或如果本機目錄的搜尋失敗，則會搜尋使用指定的目錄 **/I** CL 遇到它們的順序 選項，在命令列。

1. 中指定的目錄**INCLUDE**環境變數。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **一般**屬性頁。

1. 修改**其他 Include 目錄**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。

## <a name="example"></a>範例

下列命令會尋找 MAIN.c 要求依下列順序的 include 檔案：首先，如果使用雙引號來指定，就會搜尋本機檔案。 接下來，搜尋會繼續在 \INCLUDE 目錄中，然後在 \MY\INCLUDE 目錄中，以及最後在目錄中指派給 INCLUDE 環境變數。

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器的命令列語法](compiler-command-line-syntax.md)
