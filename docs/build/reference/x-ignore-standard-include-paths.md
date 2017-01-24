---
title: "/X (忽略標準 Include 路徑) | Microsoft Docs"
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
  - "/x"
  - "VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath"
  - "VC.Project.VCCLWCECompilerTool.IgnoreStandardIncludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/X 編譯器選項 [C++]"
  - "忽略標準 Include 路徑編譯器選項"
  - "Include 目錄, 忽略標準的"
  - "Include 檔, 忽略標準的路徑"
  - "X 編譯器選項"
  - "-X 編譯器選項 [C++]"
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /X (忽略標準 Include 路徑)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

防止編譯器在 PATH 和 INCLUDE 環境變數中指定的目錄中搜尋 include 檔。  
  
## 語法  
  
```  
/X  
```  
  
## 備註  
 您可以使用這個選項搭配 [\/I \(其他 Include 目錄\)](../../build/reference/i-additional-include-directories.md) \(**\/I**`directory`\) 選項。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**前置處理器**\] 屬性頁。  
  
4.  修改 \[**忽略標準的 Include 路徑**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。  
  
## 範例  
 在以下命令中，`/X` 是告訴編譯器忽略 PATH 和 INCLUDE 環境變數指定的位置，而 `/I` 則是指定要在其中搜尋包含檔的目錄：  
  
```  
CL /X /I \ALT\INCLUDE MAIN.C  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)