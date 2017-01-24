---
title: "/EP (前置處理至 stdout 不加 #line 指示詞) | Microsoft Docs"
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
  - "/ep"
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EP 編譯器選項 [C++]"
  - "複製前置處理器輸出至 stdout"
  - "EP 編譯器選項 [C++]"
  - "-EP 編譯器選項 [C++]"
  - "前置處理器輸出, 複製至 stdout"
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /EP (前置處理至 stdout 不加 #line 指示詞)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前置處理 C 和 C\+\+ 原始程式檔，並將前置處理過的檔案複製至標準輸出裝置。  
  
## 語法  
  
```  
/EP  
```  
  
## 備註  
 在這個處理序中會執行所有前置處理器指示詞 \(Preprocessor Directive\)，展開巨集，並且移除註解。  若要在前置處理過的輸出中保留註解，請配合 **\/EP** 使用 [\/C \(前置處理時保留註解\)](../../build/reference/c-preserve-comments-during-preprocessing.md) 選項。  
  
 **\/EP** 選項會隱藏編譯。  您必須重新送出前置處理過的檔案，進行編譯。  **\/EP** 也會隱藏 **\/FA**、**\/Fa** 和 **\/Fm** 選項的輸出檔。  如需詳細資訊，請參閱[\/FA、\/Fa \(清單檔\)](../../build/reference/fa-fa-listing-file.md)與[\/Fm \(命名對應檔\)](../../build/reference/fm-name-mapfile.md)。  
  
 在處理的稍後階段中產生的錯誤會參考前置處理過的檔案的行號，而不是原來的原始程式檔。  如果要讓行號指向原來的原始程式檔，請改用 [\/E \(前置處理至 stdout\)](../../build/reference/e-preprocess-to-stdout.md)。  **\/E** 選項會針對這個目的將 `#line` 指示詞加入至輸出。  
  
 若要將具有 `#line` 指示詞的前置處理輸出傳送至檔案，請改用 [\/P \(前置處理至檔案\)](../../build/reference/p-preprocess-to-a-file.md) 選項。  
  
 若要將具有 `#line` 指示詞的前置處理輸出傳送至 stdout，請同時使用 **\/P** 和 **\/EP**。  
  
 您無法配合 **\/EP** 選項使用先行編譯標頭。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**前置處理器**\] 屬性頁。  
  
4.  修改 \[**產生前置處理過的檔案**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## 範例  
 以下命令列會前置處理檔案 `ADD.C`，保留註解，並且將結果顯示在標準輸出裝置上：  
  
```  
CL /EP /C ADD.C  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)