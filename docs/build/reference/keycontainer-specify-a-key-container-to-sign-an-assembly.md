---
title: "/KEYCONTAINER (指定金鑰容器以簽署組件) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.KeyContainer"
  - "/keycontainer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/KEYCONTAINER 連結器選項"
  - "KEYCONTAINER 連結器選項"
  - "-KEYCONTAINER 連結器選項"
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /KEYCONTAINER (指定金鑰容器以簽署組件)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/KEYCONTAINER:name  
```  
  
## 備註  
 其中：  
  
 *name*  
 包含金鑰的容器。  若字串包含空白，請將它置於雙引號內 \(" "\)。  
  
## 備註  
 連結器將公開金鑰插入組件資訊清單內，並以私密金鑰簽署最後的組件，以建立簽署的組件。  若要產生金鑰檔，請在命令列中輸入 [sn \-k](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) `file`。  **sn \-i** 會將金鑰組 \(Key Pair\) 安裝到容器中。  
  
 若您以 [\/LN](../../build/reference/ln-create-msil-module.md) 進行編譯，則金鑰檔的名稱會儲存於模組內並加入至組件內，該組件是在編譯組件時透過 [\#using](../../preprocessor/hash-using-directive-cpp.md) 將明確參考加入至模組，或以 [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) 連結時所建立的。  
  
 您也可使用 [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 將加密資訊傳給編譯器。  若您需要部分簽署的組件，請使用 [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)。  如需組件簽署的詳細相關資訊，請參閱[強式名稱組件 \(組件簽署\)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 其他會影響組件產生的連結器選項為：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
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