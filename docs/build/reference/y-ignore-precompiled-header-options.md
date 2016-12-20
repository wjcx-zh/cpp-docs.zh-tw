---
title: "/Y- (忽略先行編譯標頭選項) | Microsoft Docs"
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
  - "/y-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Y- 編譯器選項 [C++]"
  - "-Y- 編譯器選項 [C++]"
  - "Y- 編譯器選項 [C++]"
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Y- (忽略先行編譯標頭選項)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會讓所有其他 `/Y` 編譯器選項都被忽略 \(而且本身不能覆寫\)。  
  
## 語法  
  
```  
/Y-  
```  
  
## 備註  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [\/Y \(先行編譯標頭\)](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)