---
title: /doc (處理文件註解) (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
ms.openlocfilehash: 39b614b1ab21a654a35e30b0d3acffa15d244fb0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530035"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (處理文件註解) (C/C++)

在原始程式碼檔案，並建立具有文件註解每個來源的程式碼檔案的.xdc 檔案可讓編譯器處理文件註解。

## <a name="syntax"></a>語法

> **/doc**[*名稱*]

## <a name="arguments"></a>引數

*name*<br/>
編譯器會建立.xdc 檔的名稱。 在編譯中傳遞一個.cpp 檔案時，則唯一有效。

## <a name="remarks"></a>備註

.Xdc 檔都會處理到 xdcmake.exe 的.xml 檔案。 如需詳細資訊，請參閱 < [XDCMake 參考](../../ide/xdcmake-reference.md)。

您可以將文件註解新增至您的原始程式碼檔。 如需詳細資訊，請參閱 [建議使用的文件註解標籤](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。

若要使用 IntelliSense 產生的.xml 檔案，請與您想要支援將.xml 檔案的組件相同的組件相同的目錄中的.xml 檔案的檔案名稱。 當 Visual Studio 專案中參考組件時，會也會找到.xml 檔案。 如需詳細資訊，請參閱 <<c0> [ 使用 IntelliSense](/visualstudio/ide/using-intellisense)並[提供的 XML 程式碼註解](/visualstudio/ide/supplying-xml-code-comments)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **輸出檔**屬性頁。

1. 修改**產生的 XML 文件檔**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)