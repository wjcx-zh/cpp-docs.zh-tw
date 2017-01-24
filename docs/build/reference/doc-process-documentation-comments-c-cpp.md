---
title: "/doc (處理文件註解) (C/C++) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles"
  - "/doc"
  - "VC.Project.VCCLCompilerTool.XMLDocumentationFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/doc 編譯器選項 [C++]"
  - "註解, C++ 程式碼"
  - "-doc 編譯器選項 [C++]"
  - "XML 文件, 原始程式檔中的註解"
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /doc (處理文件註解) (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會讓編譯器處理原始程式檔中的文件註解，並為每一個有文件註解的原始程式檔建立 .xdc 檔。  
  
## 語法  
  
```  
/doc[name]  
```  
  
## Arguments  
 `name`  
 編譯器將建立的 .xdc 檔案名稱。  只有在編譯中已傳遞了一個 .cpp 檔案時，才會有效。  
  
## 備註  
 .xdc 檔是以 xdcmake.exe 處理過並送入 .xml 檔中。  如需詳細資訊，請參閱[XDCMake 參考](../../ide/xdcmake-reference.md)。  
  
 您可以將文件註解加入原始程式檔。  如需詳細資訊，請參閱[建議使用的文件註解標籤](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  
  
 **\/doc** 與 **\/clr:oldSyntax** 不相容。如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 若要將所產生的 .xml 檔案搭配 IntelliSense 運用，就必須讓這個 .xml 檔案和您所要支援的組件具有相同名稱，並將這個 .xml 檔案放入與該組件相同的目錄中。  在 Visual Studio 專案中參考此組件時，就可以同時找到 .xml 檔案。  如需詳細資訊，請參閱[使用 IntelliSense](../Topic/Using%20IntelliSense.md)與[提供 XML 程式碼註解](../Topic/Supplying%20XML%20Code%20Comments.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 \[**C\/C\+\+**\] 節點。  
  
4.  按一下 \[**輸出檔**\] 屬性頁。  
  
5.  修改 \[**產生 XML 文件檔**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)