---
title: "/Oi (產生內建函式) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions"
  - "/oi"
  - "VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Oi 編譯器選項 [C++]"
  - "產生內建函式編譯器選項 [C++]"
  - "內建函式, 產生"
  - "Oi 編譯器選項 [C++]"
  - "-Oi 編譯器選項 [C++]"
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Oi (產生內建函式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

會以內建或可協助應用程式快速執行之其他特殊形式的函式取代一些函式呼叫。  
  
## 語法  
  
```  
/Oi[-]  
```  
  
## 備註  
 使用內建函式的程式會比較快速，因為它們沒有函式呼叫的額外負荷，但是也會因為額外建立的程式碼而比較大一些。  
  
 如需具有內建形式之函式的詳細資訊，請參閱 [intrinsic](../../preprocessor/intrinsic.md)。  
  
 **\/Oi** 只是要求編譯器以內建取代一些函式呼叫；如果函式可以產生更高效能，編譯器還是可以呼叫函式 \(而不以內建取代函式呼叫\)。  
  
 **x86 專屬資訊**  
  
 內建浮點函式不會對輸入值執行任何特殊檢查，所以必須在限制的輸入範圍內運作，並且擁有不同於具有相同名稱之程式庫常式的例外狀況處理和界限條件。  使用真正的內建形式意味著會喪失 IEEE 例外狀況處理，並且也會喪失 `_matherr` 和 `errno` 功能，而後者也意味著喪失 ANSI 一致性。  然而，內建形式可以顯著地加快浮點密集程式，而且對於許多程式而言，一致性的問題並沒有多少實用價值。  
  
 您可以使用 [Za](../../build/reference/za-ze-disable-language-extensions.md) 編譯器選項，覆寫真正內建浮點選項的產生。  在這種情況下，函式會產生為程式庫常式，將引數直接傳遞至浮點晶片，而不是將引數推送至程式堆疊。  
  
 **x86 專屬資訊結束**  
  
 您也可以使用 [intrinsic](../../preprocessor/intrinsic.md) 建立內建函式，或使用 [函式](../../preprocessor/function-c-cpp.md) 明確地強制執行函式呼叫。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**啟用內建函式**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器內建](../../intrinsics/compiler-intrinsics.md)