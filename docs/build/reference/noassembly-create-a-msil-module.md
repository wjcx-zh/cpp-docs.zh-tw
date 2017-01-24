---
title: "/NOASSEMBLY (建立 MSIL 模組) | Microsoft Docs"
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
  - "/NOASSEMBLY"
  - "VC.Project.VCLinkerTool.TurnOffAssemblyGeneration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOASSEMBLY 連結器選項"
  - "組件 [C++]"
  - "組件 [C++], 不是建立組件"
  - "NOASSEMBLY 連結器選項"
  - "-NOASSEMBLY 連結器選項"
ms.assetid: 3cea4e70-f451-4395-a626-1930b1b127fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOASSEMBLY (建立 MSIL 模組)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOASSEMBLY  
```  
  
## 備註  
 \/NOASSEMBLY 選項會告訴連結器為目前的輸出檔建立不含 .NET Framework 組件的映像。  沒有組件資訊清單 \(Assembly Manifest\) 的 MSIL 輸出檔稱為模組。  
  
 預設將會建立一個組件。  您也可以使用 [\/LN \(建立 MSIL 模組\)](../../build/reference/ln-create-msil-module.md) 編譯器選項，建立模組。  
  
 其他會影響組件產生的連結器選項為：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[進階\] 屬性頁。  
  
4.  修改 \[關閉組件產生\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TurnOffAssemblyGeneration%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)