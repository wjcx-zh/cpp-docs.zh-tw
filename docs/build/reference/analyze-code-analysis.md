---
title: "/analyze (程式碼分析) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnablePREfast"
  - "/analyze"
  - "VC.Project.VCCLCompilerTool.PREfastAdditionalOptions"
  - "VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/analyze 編譯器選項 [C++]"
  - "analyze 編譯器選項 [C++]"
  - "-analyze 編譯器選項 [C++]"
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# /analyze (程式碼分析)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

啟用程式碼分析和控制選項。  
  
## 語法  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## 引數  
 \/analyze  
 以預設模式開啟分析。  分析會輸出至 \[**輸出**\] 視窗，就像其他錯誤訊息一樣。  使用 **\/analyze\-** 可明確關閉分析。  
  
 \/analyze:WX\-  
 指定 **\/analyze:WX\-** 表示當您使用 **\/WX** 編譯時，程式碼分析警告不會視為錯誤。  如需詳細資訊，請參閱 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../../build/reference/compiler-option-warning-level.md)。  
  
 \/analyze:log `filename`  
 詳細的分析器結果會做為 XML 寫入至 `filename` 所指定的檔案。  
  
 \/analyze:quiet  
 關閉輸出至 \[**輸出**\] 視窗的分析器輸出。  
  
 \/analyze:stacksize `number`  
 搭配這個選項使用的 `number` 參數會指定對其產生 [C6262](../Topic/C6262.md) 警告之堆疊框架的大小 \(以位元組為單位\)。  如果未指定這個參數，則預設的堆疊框架大小為 16KB。  
  
 \/analyze:max\_paths `number`  
 搭配這個選項使用的 `number` 參數會指定要分析的程式碼路徑數目上限。  如果未指定這個參數，則預設數目為 256。  值越大，執行的檢查就越徹底，但是也可能需要較長的時間進行分析。  
  
 \/analyze:only  
 通常，編譯器在執行分析器之後，會產生程式碼並進行更多語法檢查。  **\/analyze:only** 選項會關閉這個程式碼產生階段，這樣可讓分析加快，但是也就不會發出編譯器的程式碼產生階段可能找到的編譯錯誤和警告。  如果程式並不是沒有程式碼產生錯誤，分析結果可能就不可靠，因此，建議您只有在程式碼已通過程式碼產生語法檢查且沒有錯誤的情況下，才使用這個選項。  
  
## 備註  
 如需詳細資訊，請參閱 [C\/C\+\+ 程式碼分析概觀](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md)和 [C\/C\+\+ 程式碼分析警告](../Topic/Code%20Analysis%20for%20C-C++%20Warnings.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 \[**程式碼分析**\] 節點。  
  
4.  選取 \[**一般**\] 屬性頁。  
  
5.  修改一個或多個 \[**程式碼分析**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)