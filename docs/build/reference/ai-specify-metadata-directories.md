---
title: "/AI (指定中繼資料目錄) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.AdditionalUsingDirectories"
  - "VC.Project.VCNMakeTool.AssemblySearchPath"
  - "/AI"
  - "VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/AI 編譯器選項 [C++]"
  - "AI 編譯器選項 [C++]"
  - "-AI 編譯器選項 [C++]"
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /AI (指定中繼資料目錄)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定編譯器要搜尋的目錄，以解析傳遞給 `#using` 指示詞的檔案參考。  
  
## 語法  
  
```  
/AIdirectory  
```  
  
## 引數  
 `directory`  
 編譯器要搜尋的目錄或路徑。  
  
## 備註  
 只能傳遞一個目錄給 **\/AI** 引動過程。  針對每一個您要編譯器搜尋的路徑指定一個 **\/AI** 選項。  例如，若要將 C:\\Project\\Meta 和 C:\\Common\\Meta 加入至 `#using` 指示詞的編譯器搜尋路徑，請將 `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` 加入至編譯器命令列或將每個目錄加入至 Visual Studio 中的 \[**其他 \#using 目錄**\] 屬性。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在巡覽窗格中，選取 \[**組態屬性**\]、\[**C\/C\+\+**\]、\[**一般**\]。  
  
3.  修改 \[**其他 \#using 目錄**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)