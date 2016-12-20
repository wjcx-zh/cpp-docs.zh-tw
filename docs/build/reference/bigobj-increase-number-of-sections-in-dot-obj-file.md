---
title: "/bigobj (增加 .Obj 檔中的區段數目) | Microsoft Docs"
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
  - "/bigobj"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/bigobj 編譯器選項 [C++]"
  - "bigobj 編譯器選項 [C++]"
  - "-bigobj 編譯器選項 [C++]"
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /bigobj (增加 .Obj 檔中的區段數目)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/bigobj** 可增加目的檔能夠包含的區段數目。  
  
## 語法  
  
```  
/bigobj  
```  
  
## 備註  
 目的檔預設為最多能夠存放 65,536 \(2^16\) 可定址區段，  這是目標平台指定的大小寫的問題。  **\/bigobj** 將該位址容量增加到 4,294,967,296 \(2^32\)。  
  
 大部分模組永遠都不會產生包含超過 65,536 區段的 .obj 檔。  但電腦產生的程式碼，或是大量使用樣板程式庫的程式碼，可能會需要能夠存放更多區段的 .obj 檔。  因為電腦產生的 XAML 程式碼包含大量標頭，預設**\/bigobj** 在 Windows 市集專案為啟用。  如果您停用 Windows 市集應用程式專案中這個選項可能發生編譯器錯誤 C1128。  
  
 在 Visual C\+\+ 2005 以前隨附的連結器無法讀取透過 **\/bigobj** 產生的 .obj 檔。  
  
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