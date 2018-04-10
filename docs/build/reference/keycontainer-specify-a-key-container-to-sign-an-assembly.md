---
title: -KEYCONTAINER （指定金鑰容器以簽署組件） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs:
- C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f0e1f31e85c23b32bee1b8b968bbec65ee82beb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (指定金鑰容器以簽署組件)
```  
/KEYCONTAINER:name  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *name*  
 包含索引鍵的容器。 將字串置於雙引號內 ("") 如果包含空格。  
  
## <a name="remarks"></a>備註  
 連結器建立公開金鑰插入組件資訊清單，並使用私密金鑰簽署最終組件簽署的組件。 若要產生的金鑰檔案，請輸入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令列。 **sn-i**金鑰組安裝至容器。  
  
 如果您使用編譯[/LN](../../build/reference/ln-create-msil-module.md)，金鑰檔的名稱是保留在模組中，而且併入編譯的組件所包含的明確參考到模組，透過時所建立的組件[#using](../../preprocessor/hash-using-directive-cpp.md)，或使用連結時[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。  
  
 您也可以傳遞給您的加密資訊與編譯器[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)。 使用[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)如果您想要的部分簽署組件。 請參閱[強式名稱組件 （組件簽署） (C + + /CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)如需有關簽署組件。  
  
 其他會影響產生的組件的連結器選項包括：  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)