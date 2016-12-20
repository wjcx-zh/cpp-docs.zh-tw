---
title: "/showIncludes (列示包含檔) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.ShowIncludes"
  - "VC.Project.VCCLCompilerTool.ShowIncludes"
  - "/showincludes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/showIncludes 編譯器選項 [C++]"
  - "Include 檔"
  - "Include 檔, 在編譯時顯示"
  - "showIncludes 編譯器選項 [C++]"
  - "-showIncludes 編譯器選項 [C++]"
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /showIncludes (列示包含檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讓編譯器輸出 include 檔的清單。  巢狀包含檔也會顯示 \(您包含的檔案中所包含的檔案\)。  
  
## 語法  
  
```  
/showIncludes  
```  
  
## 備註  
 在編譯時碰到包含檔時，便會輸出一個訊息，例如：  
  
```  
Note: including file: d:\MyDir\include\stdio.h  
```  
  
 巢狀 include 檔會以縮排表示，巢狀的每一層加一個空格，例如：  
  
```  
Note: including file: d:\temp\1.h  
Note: including file:  d:\temp\2.h  
```  
  
 在這個範例中，`2.h` 是從 `1.h` 包含納入，所以加上縮排。  
  
 The **\/showIncludes** 選項是發出至 `stderr`，不是 `stdout`。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[**顯示 Include 檔**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)