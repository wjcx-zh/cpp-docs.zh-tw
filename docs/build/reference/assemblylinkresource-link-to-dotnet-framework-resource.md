---
title: -ASSEMBLYLINKRESOURCE （連結到.NET Framework 資源） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
dev_langs:
- C++
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a922ac1a96a59d574f46f7b04db8b160a5079918
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374046"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)
```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 您要從組件連結的目標 .NET Framework 資源檔。  
  
## <a name="remarks"></a>備註  
 /ASSEMBLYLINKRESOURCE 選項會建立輸出檔案中的.NET Framework 資源的連結資源檔不被放在輸出檔。 [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)資源檔嵌入輸出檔。  
  
 連結的資源為公用時，連結器在建立組件中。  
  
 /ASSEMBLYLINKRESOURCE 時必須編譯包含[/clr](../../build/reference/clr-common-language-runtime-compilation.md);[/LN](../../build/reference/ln-create-msil-module.md)或[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) /ASSEMBLYLINKRESOURCE 不允許。  
  
 如果*filename*是.NET Framework 建立的資源檔，例如，藉由[Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) ，或是在開發環境中，它可以存取與其中成員保持**System.Resources**命名空間。 如需詳細資訊，請參閱[System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx)。 如需其他資源，使用**GetManifestResource** \*方法**System.Reflection.Assembly**類別，以在執行階段存取資源。  
  
 *檔名*可以是任何檔案格式。 例如，您可以產生組件，原生 DLL 部分，以便將它安裝到全域組件快取，並從組件中的 managed 程式碼存取。  
  
 其他會影響產生的組件的連結器選項包括：  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)