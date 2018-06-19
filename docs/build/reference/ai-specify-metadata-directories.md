---
title: -AI （指定中繼資料目錄） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
dev_langs:
- C++
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bde5c93c8a211bb0fc66028932a0a7d50415236d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369428"
---
# <a name="ai-specify-metadata-directories"></a>/AI (指定中繼資料目錄)
指定編譯器要搜尋的目錄，以解析傳遞給 `#using` 指示詞的檔案參考。  
  
## <a name="syntax"></a>語法  
  
```  
/AIdirectory  
```  
  
## <a name="arguments"></a>引數  
 `directory`  
 編譯器要搜尋的目錄或路徑。  
  
## <a name="remarks"></a>備註  
 只有一個目錄可以傳遞至 **/AI**引動過程。 指定一個 **/AI**每一個您要編譯器搜尋的路徑的選項。 例如，若要將 C:\Project\Meta 和 C:\Common\Meta 加入至編譯器搜尋路徑`#using`指示詞加入`/AI"C:\Project\Meta" /AI"C:\Common\Meta"`編譯器命令列新增至每個目錄或**其他 #using 目錄**在 Visual Studio 中的屬性。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  瀏覽窗格中，選取**組態屬性**， **C/c + +**，**一般**。  
  
3.  修改**其他 #using 目錄**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)