---
title: "/FU (命名強制的 #using 檔案) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.ForcedUsingFiles"
  - "/FU"
  - "VC.Project.VCNMakeTool.ForcedUsingAssemblies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FU 編譯器選項 [C++]"
  - "FU 編譯器選項 [C++]"
  - "-FU 編譯器選項 [C++]"
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FU (命名強制的 #using 檔案)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以作為替代方式的編譯器選項，來傳遞檔名給原始程式碼中的 [\#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。  
  
## 語法  
  
```  
/FU file  
```  
  
## Arguments  
 `file`  
 指定要在這個編譯中參考的中繼資料檔。  
  
## 備註  
 \/FU 參數只需一個檔名。  若要指定多個檔案，請使用與每一個 \/FU。  
  
 如果您使用 [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] 和參考中繼資料來使用 [Friend 組件](../../dotnet/friend-assemblies-cpp.md) 功能，您不能使用 **\/FU**。  您必須參考中繼資料在程式碼中使用 `#using`—一起使用 `[as friend]` 屬性。  Friend 組件不支援於 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\) 。  
  
 如需關於為 Common Language Runtime\(CLR\) 建立組件或模組的詳細資訊，請參閱 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  如需如何在 [!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]中建置的詳細資訊，請參閱[建置應用程式和程式庫](../Topic/Building%20apps%20and%20libraries%20\(C++-CX\).md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  請選取 \[**進階**\] 屬性頁。  
  
4.  修改 \[**強制 \#using**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>。  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)