---
title: "-ASSEMBLYMODULE （將 MSIL 模組加入組件） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
dev_langs: C++
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9709a98ee6528a2081f98351126cc84529b0733b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (將 MSIL 模組加入組件)
```  
/ASSEMBLYMODULE:filename  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 *filename*  
 想要包含在這個組件中的模組。  
  
## <a name="remarks"></a>備註  
 /ASSEMBLYMODULE 選項可讓您加入組件的模組參考。 模組中的類型資訊將無法使用加入的模組參考的組件程式。 不過，在模組中的類型資訊將可參考的組件的任何程式。  
  
 使用[#using](../../preprocessor/hash-using-directive-cpp.md)加入組件的模組參考和組件程式提供的模組類型資訊。  
  
 例如，請考慮下列案例：  
  
1.  建立同名的模組[/LN](../../build/reference/ln-create-msil-module.md)。  
  
2.  使用不同的專案中的 /ASSEMBLYMODULE 来包含在目前的編譯中，將會建立組件的模組。 這個專案不會參照的模組`#using`。  
  
3.  參考這個組件的任何專案現在也可以使用從模組的類型。  
  
 其他會影響產生的組件的連結器選項包括：  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Visual C++ 連結器接受 .netmodule 檔案做為輸入，而連結器產生的輸出檔將是組件或 .netmodule (對連結器的任何輸入 .netmodule 沒有執行階段相依性)。  如需詳細資訊，請參閱 [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**輸入**屬性頁。  
  
4.  修改**將模組加入組件**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)