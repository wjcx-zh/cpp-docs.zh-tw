---
title: "最佳化程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, 效能"
  - "程式碼, 最佳化"
  - "最佳化"
  - "最佳化, C++ 程式碼"
  - "效能, 編譯器"
  - "效能, 最佳化程式碼"
ms.assetid: 4f33e6c7-9870-43b3-9c2f-d7e44f764971
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 最佳化程式碼
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

透過最佳化程式碼，您可以在程式碼執行速度和大小之間取得平衡。  本主題討論 Visual C\+\+ 在協助最佳化程式碼方面提供的部分機制。  
  
## 語言功能  
 下列主題描述 C\/C\+\+ 語言中的一些最佳化功能。  
  
 [最佳化 Pragma 和關鍵字](../../build/reference/optimization-pragmas-and-keywords.md)  
 關鍵字和 pragma 清單，您可以在程式碼中用來提升效能。  
  
 [依分類排列的編譯器選項](../../build/reference/compiler-options-listed-by-category.md)  
 特別會影響執行速度或程式碼大小的 **\/O** 編譯器選項清單。  
  
 [右值參考宣告子：&&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
 右值參考支援實作「*移動語意*」\(Move Semantic\)。  如果使用移動語意來實作樣板程式庫，則使用這些樣板的應用程式效能可以獲得顯著提升。  
  
### 最佳化 Pragma  
 如果程式碼的某個最佳化區段造成錯誤或拖慢速度，您可使用 [optimize](../../preprocessor/optimize.md) pragma 來關閉該區段的最佳化。  
  
 請依下列方式將程式碼置於兩個 pragma 之間：  
  
```  
#pragma optimize("", off)  
// some code here   
#pragma optimize("", on)  
```  
  
## 程式設計作法  
 您可能也注意到，當您以最佳化編譯程式碼時，會出現某些額外的警告訊息。  這是正常的行為，因為某些警告僅與最佳化的程式碼相關。  如果您留意這些警告，就可避免許多最佳化問題。  
  
 矛盾的是，為了追求速度而最佳化程式反而可能使得程式碼執行變慢。  這是因為某些速度最佳化會增加程式碼大小。  例如，內嵌函式可以減輕函式呼叫的額外負荷。  但是，內嵌過多的程式碼可能會使程式過大，而增加虛擬記憶體的分頁錯誤數目。  因此，排除函式呼叫所獲致的速度效能可能因記憶體交換而消失。  
  
 下列主題討論良好的程式設計實務。  
  
 [改善時間關鍵程式碼的秘訣](../../build/reference/tips-for-improving-time-critical-code.md)  
 優良的程式碼撰寫技巧可以獲得較佳的效能。  本主題提供了幾點程式碼撰寫建議，協助您確保程式碼具時間關鍵 \(Time Critical\) 的部分能夠有效地執行。  
  
 [最佳化最佳作法](../../build/reference/optimization-best-practices.md)  
 提供如何將應用程式最佳化的一般指引。  
  
## 偵錯最佳化的程式碼  
 由於最佳化可能會變更編譯器所建立的程式碼，因此建議您對應用程式進行偵錯並測量其效能，然後最佳化程式碼。  
  
 下列主題提供有關如何偵錯的基本資訊。  
  
-   [Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)  
  
-   [建立發行組建時的常見問題](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
 下列主題提供有關如何偵錯的更進階資訊。  
  
-   [如何：偵錯最佳化程式碼](../Topic/How%20to:%20Debug%20Optimized%20Code.md)  
  
-   [浮點數會失去精確度的原因](../../build/reference/why-floating-point-numbers-may-lose-precision.md)  
  
 下列主題類型提供如何最佳化建置、載入以及執行程式碼的相關資訊。  
  
-   [改善編譯器處理量](../../build/reference/improving-compiler-throughput.md)  
  
-   [使用不帶 \(\) 的函式名稱不會產生程式碼](../../build/reference/using-function-name-without-parens-produces-no-code.md)  
  
-   [最佳化內嵌組譯碼](../../assembler/inline/optimizing-inline-assembly.md)  
  
-   [為 ATL 專案指定編譯器最佳化](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)  
  
-   [載入時，我應該使用何項最佳化技術來改善用戶端應用程式的效能？](../../build/what-optimization-techniques-should-i-use.md)  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]若要了解如何在載入 DLL 方法時縮短時間，請參閱 [MSDN Library](http://go.microsoft.com/fwlink/?linkid=556) 網站上 "MSDN Magazine" 之 "Under the Hood" 專欄中的＜最佳化 DLL 載入時間效能＞\(英文\)。  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)]若要了解如何將應用程式中之分頁最小化，請參閱 [MSDN Library](http://go.microsoft.com/fwlink/?linkid=556) 網站上 "MSDN Magazine" 之 "Bugslayer" 專欄中的＜利用 Smooth Working Set Tool 提升執行階段效能＞和＜利用 Smooth Working Set Tool 提升執行階段效能 \(第二部分\)＞\(英文\)。  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)