---
title: "/E (前置處理至 stdout) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/e"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/E 編譯器選項 [C++]"
  - "-E 編譯器選項 [C++]"
  - "前置處理器輸出"
  - "前置處理器輸出, 複製至 stdout"
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /E (前置處理至 stdout)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前置處理 C 和 C\+\+ 原始程式檔，並將前置處理過的檔案複製至標準輸出裝置。  
  
## 語法  
  
```  
/E  
```  
  
## 備註  
 在這個處理序中，所有前置處理器指示詞 \(Preprocessor Directive\) 都會加以執行，巨集也會展開，註解則會移除。  若要在前置處理過的輸出中保留註解，請同時使用 [\/C \(前置處理時保留註解\)](../../build/reference/c-preserve-comments-during-preprocessing.md) 選項。  
  
 **\/E** 會將 `#line` 指示詞加入至輸出，在每一個包含納入之檔案的開頭和結尾，以及環繞於前置處理器指示詞所移除的行，以進行條件式編譯。  這些指示詞會重編經前置處理之檔案的行號，  因此在處理稍後階段中產生的錯誤會參考原來的原始程式檔中的行號，而不是經前置處理過的檔案中的行。  
  
 **\/E** 選項會隱藏編譯。  您必須重新送出前置處理過的檔案，進行編譯。  **\/E** 也會隱藏 **\/FA**、**\/Fa** 和 **\/Fm** 選項的輸出檔。  如需詳細資訊，請參閱[\/FA、\/Fa \(清單檔\)](../../build/reference/fa-fa-listing-file.md)與[\/Fm \(命名對應檔\)](../../build/reference/fm-name-mapfile.md)。  
  
 若要隱藏 `#line` 指示詞，請使用 [\/EP \(前置處理至 stdout 不加 \#line 指示詞\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 選項取代。  
  
 若要將前置處理過的輸出傳送至檔案而不傳遞至 `stdout`，請改用 [\/P \(前置處理至檔案\)](../../build/reference/p-preprocess-to-a-file.md) 選項。  
  
 若要隱藏 `#line` 指示詞，並將前置處理過的輸出傳送至檔案，請同時使用 **\/P** 和 **\/EP**。  
  
 您不能配合 **\/E** 選項使用先行編譯標頭。  
  
 請注意，在前置處理一個單獨的檔案時，語彙基元 \(Token\) 後面不會產生空格，  這樣可能會產生不合法的程式或具有不想要的副作用。  下列程式會順利編譯成功：  
  
```  
#define m(x) x  
m(int)main( )  
{  
   return 0;  
}  
```  
  
 但是，如果您是以下列方式編譯：  
  
```  
cl -E test.cpp > test2.cpp  
```  
  
 test2.cpp 中的 `int main` 將會在錯誤的情況下成為 `intmain`。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>。  
  
## 範例  
 以下命令列會前置處理 `ADD.C`、保留註解、加入 `#line` 指示詞，並且將結果顯示在標準輸出裝置上：  
  
```  
CL /E /C ADD.C  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)