---
title: /AI (指定中繼資料目錄)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
ms.openlocfilehash: a2d87039e2195c96e4209c7b5098473a6f52c486
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424440"
---
# <a name="ai-specify-metadata-directories"></a>/AI (指定中繼資料目錄)

指定編譯器要搜尋的目錄，以解析傳遞給 `#using` 指示詞的檔案參考。

## <a name="syntax"></a>語法

> **/AI**_directory_

## <a name="arguments"></a>引數

*directory*<br/>
編譯器要搜尋的目錄或路徑。

## <a name="remarks"></a>備註

只有一個目錄可以傳遞給 **/AI**引動過程。 請指定其中一個 **/AI**選項針對每個您想要編譯器搜尋的路徑。 例如，若要將 C:\Project\Meta 和 C:\Common\Meta 加入至編譯器搜尋路徑`#using`指示詞，新增`/AI"C:\Project\Meta" /AI"C:\Common\Meta"`至編譯器命令列或新增至每個目錄**其他 #using 目錄**在 Visual Studio 中的屬性。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **一般**屬性頁。

1. 修改**其他 #using 目錄**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)<br/>
[#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)
