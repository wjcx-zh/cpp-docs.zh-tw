---
title: "/ASSEMBLYRESOURCE (內嵌 Managed 資源) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.EmbedManagedResourceFile"
  - "/ASSEMBLYRESOURCE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYRESOURCE 連結器選項"
  - "組件 [C++]"
  - "組件 [C++], 連結資源檔"
  - "ASSEMBLYRESOURCE 連結器選項"
  - "-ASSEMBLYRESOURCE 連結器選項"
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /ASSEMBLYRESOURCE (內嵌 Managed 資源)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## 參數  
 *filename*  
 您要內嵌到這個組件內的 Managed 資源。  
  
 *name*  
 選擇項。  資源的邏輯名稱；用來載入資源的名稱。  預設值是檔案的名稱。  
  
 或者，您也可以指定檔案在組件資訊清單 \(Assembly Manifest\) 中是否應為私用 \(Private\)。  依預設，*name* 在組件中是公用的。  
  
## 備註  
 請使用 \/ASSEMBLYRESOURCE 選項將資源內嵌到組件。  
  
 資源如果是以連結器建立的，它在組件中將會是公用的。  連結器不允許您重新命名組件中的資源。  
  
 假設 *filename* 是由[資源檔產生器 \(Resgen.exe\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) 或在開發環境中所建立的 .NET Framework 資源檔，它可以使用 **System.Resources** 命名空間內的成員來存取 \(如需詳細資訊，請參閱 [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx)\)。  其他所有的資源，則可以在 Run Time 時使用 **System.Reflection.Assembly** 類別的 **GetManifestResource\*** 方法來存取資源。  
  
 其他會影響組件產生的連結器選項為：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[輸入\] 屬性頁。  
  
4.  修改 \[嵌入 Managed 資源檔\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)