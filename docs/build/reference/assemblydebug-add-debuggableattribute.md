---
title: "/ASSEMBLYDEBUG (加入 DebuggableAttribute) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.AssemblyDebug"
  - "/ASSEMBLYDEBUG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYDEBUG 連結器選項"
  - "ASSEMBLYDEBUG 連結器選項"
  - "-ASSEMBLYDEBUG 連結器選項"
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ASSEMBLYDEBUG (加入 DebuggableAttribute)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYDEBUG[:DISABLE]  
```  
  
 \/ASSEMBLYDEBUG 會發出帶有偵錯資訊追蹤的 **DebuggableAttribute** 屬性，並停用 JIT 最佳化。  如此便和在原始碼中指定下列屬性一樣：  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
 \/ASSEMBLYDEBUG:DISABLE 會發出 **DebuggableAttribute** 屬性，但停用偵錯資訊追蹤，而啟用 JIT 最佳化。  如此便和在原始碼中指定下列屬性一樣：  
  
```  
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE  
```  
  
 預設值是不發出 **DebuggableAttribute** 屬性。  
  
 DebuggableAttribute 也可直接加入至原始程式碼中的組件。  例如：  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
## 備註  
 在 Visual C\+\+ .NET 2003 \(含\) 以上版本中，必須明確指定 Managed 影像可偵錯。  只使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 是不夠的。  
  
 其他會影響組件產生的連結器選項為：  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[偵錯\] 屬性頁。  
  
4.  修改 \[可偵錯組件\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)