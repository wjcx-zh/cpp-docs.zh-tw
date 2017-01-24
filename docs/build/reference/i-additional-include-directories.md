---
title: "/I (其他 Include 目錄) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories"
  - "VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories"
  - "/I"
  - "VC.Project.VCNMakeTool.IncludeSearchPath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/I 編譯器選項 [C++]"
  - "其他 Include 目錄編譯器選項"
  - "I 編譯器選項 [C++]"
  - "-I 編譯器選項 [C++]"
  - "Include 目錄, 編譯器選項 [C++]"
  - "設定 Include 目錄"
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /I (其他 Include 目錄)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將目錄加入至要搜尋 include 檔的目錄清單。  
  
## 語法  
  
```  
/I[ ]directory  
```  
  
## Arguments  
 `directory`  
 是要加入到搜尋包含檔之目錄清單的目錄。  
  
## 備註  
 若要加入一個以上目錄，請重複使用這個選項。  這些目錄會逐一被搜尋直到找到指定的包含檔為止。  
  
 您可以使用這個選項配合 \[忽略標準 Include 路徑\] \([\/X \(忽略標準 Include 路徑\)](../../build/reference/x-ignore-standard-include-paths.md)\) 選項。  
  
 編譯器會依下列順序搜尋各目錄：  
  
1.  含有原始程式檔的目錄。  
  
2.  以 **\/I** 選項指定的目錄，依照 CL 所碰到的先後順序搜尋。  
  
3.  在 **INCLUDE** 環境變數中指定的目錄。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**一般**\] 屬性頁。  
  
4.  修改 \[**其他 Include 目錄**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>。  
  
## 範例  
 以下命令會依下列順序尋找 MAIN.c 要求的包含檔：首先尋找含有 MAIN.c 的目錄，然後是 \\INCLUDE 目錄，再接下來是 \\MY\\INCLUDE 目錄，最後是指派給 INCLUDE 環境變數的目錄。  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)