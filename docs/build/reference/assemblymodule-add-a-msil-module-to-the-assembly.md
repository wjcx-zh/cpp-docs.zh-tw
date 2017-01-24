---
title: "/ASSEMBLYMODULE (將 MSIL 模組加入組件) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/assemblymodule"
  - "VC.Project.VCLinkerTool.AddModuleNamesToAssembly"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYMODULE 連結器選項"
  - "組件 [C++]"
  - "組件 [C++], 加入模組至"
  - "ASSEMBLYMODULE 連結器選項"
  - "-ASSEMBLYMODULE 連結器選項"
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYMODULE (將 MSIL 模組加入組件)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYMODULE:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 您要加入這個組件中的模組。  
  
## 備註  
 \/ASSEMBLYMODULE 選項可以讓您將模組參考加入至組件。  加入模組參考的組件程式將無法使用模組中的型別資訊。  不過，參考該組件的任何程式將可以使用模組中的型別資訊。  
  
 使用 [\#using](../../preprocessor/hash-using-directive-cpp.md) 可以將模組參考加入至組件，也可以讓模組的型別資訊供組件程式使用。  
  
 例如，請考量下列案例：  
  
1.  使用 [\/LN](../../build/reference/ln-create-msil-module.md) 建立模組。  
  
2.  在另一個專案中使用 \/ASSEMBLYMODULE 以包含目前編譯 \(Compilation\) 中會建立組件的模組。  這個專案不會以 `#using` 參考該模組。  
  
3.  參考這個組件的任何專案現在也可以使用該模組的型別。  
  
 其他會影響組件產生的連結器選項為：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Visual C\+\+ 連結器接受 .netmodule 檔案做為輸入，而和連結器產生的輸出檔將是組件或 .netmodule 沒有輸入至連結器的執行階段依賴任何 .netmodules。如需詳細資訊，請參閱[.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[輸入\] 屬性頁。  
  
4.  修改 \[將模組加入組件\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)