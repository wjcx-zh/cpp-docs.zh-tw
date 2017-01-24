---
title: "/KEYFILE (指定金鑰或金鑰組以簽署組件) | Microsoft Docs"
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
  - "/keyfile"
  - "VC.Project.VCLinkerTool.KeyFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/KEYFILE 連結器選項"
  - "KEYFILE 連結器選項"
  - "-KEYFILE 連結器選項"
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /KEYFILE (指定金鑰或金鑰組以簽署組件)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/KEYFILE:filename  
```  
  
## 備註  
 其中：  
  
 *filename*  
 包含金鑰的檔案。  若字串包含空白，請將它置於雙引號內 \(" "\)。  
  
## 備註  
 連結器會將公開金鑰插入組件資訊清單內，並以私密金鑰簽署最後的組件。  若要產生金鑰檔，請在命令列中輸入 [sn \-k](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) `file`。  簽署的組件就是所謂有強式名稱 \(Strong Name\)。  
  
 若您以 [\/LN](../../build/reference/ln-create-msil-module.md) 進行編譯，則金鑰檔的名稱會儲存於模組內並加入至組件內，該組件是在編譯組件時透過 [\#using](../../preprocessor/hash-using-directive-cpp.md) 將明確參考加入至模組，或以 [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) 連結時所建立的。  
  
 您也可使用 [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) 將您的加密資訊傳給連結器。  若您需要部分簽署的組件，請使用 [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)。  如需組件簽署的詳細相關資訊，請參閱[強式名稱組件 \(組件簽署\)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 在指定了 **\/KEYFILE** 和 **\/KEYCONTAINER** 的狀況下 \(不管是透過命令列選項或自訂屬性\)，連結器都會先嘗試金鑰容器。  如果這個動作成功，那麼組件就會使用金鑰容器中的資訊加以簽署。  若連結器找不到金鑰容器，就會嘗試 \/KEYFILE 所指定的檔案。  如果此動作成功，組件會以金鑰檔內的資訊簽署，並將金鑰資訊安裝於金鑰容器內 \(類似於 sn \-i\)，以便在下次編譯時，讓金鑰容器有效。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 如需簽署組件的詳細資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
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