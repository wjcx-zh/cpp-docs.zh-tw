---
title: "-/doc （處理文件註解） （C/c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8737c0e33d33fe062d9a07f18d9005e58463f5b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (處理文件註解) (C/C++)
在原始程式碼檔，並建立.xdc 檔的每個來源的程式碼檔案具有文件註解，請讓編譯器處理文件註解。  
  
## <a name="syntax"></a>語法  
  
```  
/doc[name]  
```  
  
## <a name="arguments"></a>引數  
 `name`  
 編譯器會建立.xdc 檔的名稱。 編譯過程中傳遞一個.cpp 檔案時才有效。  
  
## <a name="remarks"></a>備註  
 .xdc 檔處理到 xdcmake.exe 與.xml 檔案。 如需詳細資訊，請參閱[XDCMake 參考](../../ide/xdcmake-reference.md)。  
  
 您可以將文件註解加入至您的原始程式碼檔。 如需詳細資訊，請參閱[建議的文件註解標記](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  
  
 若要使用 IntelliSense 產生的.xml 檔案，請與您想要支援和.xml 檔案放入的組件相同的組件相同的目錄中的.xml 檔案的檔案名稱。 Visual Studio 專案中參考組件時的.xml 檔案也可以找到。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)和[提供 XML 程式碼註解](/visualstudio/ide/supplying-xml-code-comments)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**C/c + +**節點。  
  
4.  選取**輸出檔**屬性頁。  
  
5.  修改**產生 XML 文件檔**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)