---
title: "-I (其他 Include 目錄) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs: C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfbf962a92af22d3e724c592fec6cf812b610dc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="i-additional-include-directories"></a>/I (其他 Include 目錄)
將目錄加入至搜尋 include 檔的目錄清單。  
  
## <a name="syntax"></a>語法  
  
```  
/I[ ]directory  
```  
  
## <a name="arguments"></a>引數  
 `directory`  
 要加入的目錄清單中的目錄搜尋 include 檔。  
  
## <a name="remarks"></a>備註  
 若要加入多個目錄，一次使用此選項。 目錄會搜尋才找到指定的包含檔。  
  
 您可以使用此選項以忽略標準 Include 路徑 ([/X （忽略標準 Include 路徑）](../../build/reference/x-ignore-standard-include-paths.md)) 選項。  
  
 編譯器會搜尋目錄，以下列順序：  
  
1.  包含來源檔案的目錄。  
  
2.  以指定的目錄**/I**選項，CL 碰到它們的順序。  
  
3.  中指定的目錄**INCLUDE**環境變數。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**一般**屬性頁。  
  
4.  修改**其他 Include 目錄**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。  
  
## <a name="example"></a>範例  
 下列命令會依下列順序要求 MAIN.c include 檔： 包含 MAIN.c，然後在 \INCLUDE 目錄中，然後在 \MY\INCLUDE 目錄中，以及最後的目錄中指定要包含的目錄中的第一個環境變數。  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)