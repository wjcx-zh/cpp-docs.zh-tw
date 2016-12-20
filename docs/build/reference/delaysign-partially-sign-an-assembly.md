---
title: "/DELAYSIGN (部分簽署組件) | Microsoft Docs"
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
  - "/delaysign"
  - "VC.Project.VCLinkerTool.DelaySign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYSIGN 連結器選項"
  - "DELAYSIGN 連結器選項"
  - "-DELAYSIGN 連結器選項"
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DELAYSIGN (部分簽署組件)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAYSIGN[:NO]  
```  
  
## 備註  
 其中：  
  
 NO  
 指定不應部分簽署組件。  
  
## 備註  
 若您只想要將公開金鑰 \(Public Key\) 置於組件內，請使用 **\/DELAYSIGN**。  預設值為 **\/DELAYSIGN:NO**。  
  
 **\/DELAYSIGN** 選項除非與 [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 或 [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) 一起使用，否則並沒有效用。  
  
 當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 \(組件中繼資料\) 的檔案，並且利用私密金鑰簽署該項雜湊。  所產生的數位簽章儲存在包含資訊清單的檔案中。  當組件延遲簽署時，連結器並不會計算與儲存簽章，不過會在檔案中保留空間，以方便日後加入簽章。  
  
 例如，使用 **\/DELAYSIGN** 可讓測試人員將組件放在全域快取區內。  測試過後，即可透過將私密金鑰放在組件內，為組件完整簽署。  
  
 如需為組件簽署的詳細資訊，請參閱[強式名稱組件 \(組件簽署\)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) 和[延遲簽署組件](../Topic/Delay%20Signing%20an%20Assembly.md)。  
  
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