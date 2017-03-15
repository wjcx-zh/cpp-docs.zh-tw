---
title: "/P (前置處理至檔案) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFile"
  - "/p"
  - "VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/P 編譯器選項 [C++]"
  - "輸出檔, 前置處理器"
  - "P 編譯器選項 [C++]"
  - "-P 編譯器選項 [C++]"
  - "前置處理輸出檔"
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /P (前置處理至檔案)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前置處理 C 和 C\+\+ 原始程式檔，並將前置處理過的輸出寫入檔案中。  
  
## 語法  
  
```  
/P  
```  
  
## 備註  
 該檔案具有與原始程式檔和 .i 副檔名相同的主檔名。  在這個處理序中會執行所有前置處理器指示詞 \(Preprocessor Directive\)，展開巨集，並且移除註解。  若要在前置處理過的輸出中保留註解，請同時使用 [\/C \(前置處理時保留註解\)](../../build/reference/c-preserve-comments-during-preprocessing.md) 選項以及 **\/P**。  
  
 **\/P** 會將 `#line` 指示詞加入至輸出，在每一個包含納入之檔案的開頭和結尾，以及環繞於前置處理器指示詞所移除的行，以進行條件式編譯。  這些指示詞會重編經前置處理之檔案的行號，  因此在處理稍後階段中產生的錯誤會參考原來的原始程式檔中的行號，而不是經前置處理過的檔案中的行。  若要隱藏 `#line` 指示詞的產生，請使用 [\/EP \(前置處理至 stdout 不加 \#line 指示詞\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 以及 **\/P**。  
  
 **\/P** 選項會隱藏編譯。  即使您使用了 [\/Fo \(目的檔名稱\)](../../build/reference/fo-object-file-name.md)，它也不會產生 .obj 檔案。  您必須重新送出前置處理過的檔案，進行編譯。  **\/P** 也會隱藏 **\/FA**、**\/Fa** 和 **\/Fm** 選項的輸出檔。  如需詳細資訊，請參閱[\/FA、\/Fa \(清單檔\)](../../build/reference/fa-fa-listing-file.md)與[\/Fm \(命名對應檔\)](../../build/reference/fm-name-mapfile.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**前置處理器**\] 屬性頁。  
  
4.  修改 \[**產生前置處理過的檔案**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## 範例  
 以下命令列會前置處理 `ADD.C`、保留註解、加入 `#line` 指示詞，並將結果寫入至檔案 `ADD.I`：  
  
```  
CL /P /C ADD.C  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\/Fi \(前置處理輸出檔名稱\)](../../build/reference/fi-preprocess-output-file-name.md)