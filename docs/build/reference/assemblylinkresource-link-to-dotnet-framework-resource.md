---
title: "/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ASSEMBLYLINKRESOURCE"
  - "VC.Project.VCLinkerTool.AssemblyLinkResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYLINKRESOURCE 連結器選項"
  - "ASSEMBLYLINKRESOURCE 連結器選項"
  - "-ASSEMBLYLINKRESOURCE 連結器選項"
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 您想要從該組件連結的 .NET Framework 資源檔。  
  
## 備註  
 \/ASSEMBLYLINKRESOURCE 選項會在輸出檔中建立一個 .NET Framework 資源的連結; 資源檔並不放在輸出檔中。  [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) 會在輸出檔中嵌入一個資源檔。  
  
 Linked 資源如果是以連結器建立的，則在組件中就是公用的 \(Public\)。  
  
 \/ASSEMBLYLINKRESOURCE 要求編譯包含 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md)；[\/LN](../../build/reference/ln-create-msil-module.md) 或 [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) 不允許搭配 \/ASSEMBLYLINKRESOURCE。  
  
 假設 *filename* 是由 [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在開發環境中所建立的 .NET Framework 資源檔，就可以使用 **System.Resources** 命名空間內的成員來存取。  如需詳細資訊，請參閱 [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx)。  其他所有的資源，則可以在執行階段時使用 **System.Reflection.Assembly** 類別的 **GetManifestResource\*** 方法來存取資源。  
  
 *filename* 的檔案格式不拘。  例如，您可能要讓原生 DLL 成為組件的一部分，以便將它安裝到全域組件快取中，並從組件中的 Managed 程式碼存取。  
  
 其他會影響組件產生的連結器選項為：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)