---
title: "-KEYFILE （指定金鑰或金鑰組簽署組件） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
dev_langs: C++
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86457510eb017fe2d5060f2f37661a3397ec30d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (指定金鑰或金鑰組以簽署組件)
```  
/KEYFILE:filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 包含索引鍵的檔案。 將字串置於雙引號內 ("") 如果包含空格。  
  
## <a name="remarks"></a>備註  
 連結器將公開金鑰插入組件資訊清單，然後使用私密金鑰簽署最終組件。 若要產生的金鑰檔案，請輸入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令列。 即所謂具有強式名稱簽署組件。  
  
 如果您使用編譯[/LN](../../build/reference/ln-create-msil-module.md)，金鑰檔的名稱是保留在模組中，而且併入編譯的組件所包含的明確參考到模組，透過時所建立的組件[#using](../../preprocessor/hash-using-directive-cpp.md)，或使用連結時[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。  
  
 您也可以將加密資訊傳遞至連結器使用[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)。 使用[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)如果您想要的部分簽署組件。 請參閱[強式名稱組件 （組件簽署） (C + + /CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)如需有關簽署組件。  
  
 在案例同時**/KEYFILE**和**/KEYCONTAINER**指定連結器 （命令列選項或是自訂屬性），會先嘗試金鑰容器。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。 如果連結器找不到金鑰容器，將會嘗試 /KEYFILE 與指定的檔案。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件，並將金鑰資訊安裝在金鑰容器中 (類似於 sn -i)，這樣在下次編譯時，金鑰容器就會是有效的。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 請參閱[Creating and using strong-named Assemblies](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)如需有關簽署組件。  
  
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