---
title: "演算法 | Microsoft Docs"
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
  - "演算法樣板函式 C++ 程式庫慣例"
  - "演算法 [C++], C++"
  - "慣例 [C++], C++ 演算法"
  - "程式庫 [C++], C++ 演算法慣例"
  - "Standard C++ 程式庫, 演算法"
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演算法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

演算法是標準範本程式庫的基礎部分。  演算法不會對容器本身執行，而是對迭代器執行。  因此，相同的演算法可供大部分、甚至所有的 STL 容器使用。  本節討論 STL 演算法的慣例和術語。  
  
## 備註  
 在說明演算法範本函式時會使用數個速記片語：  
  
-   片語「在範圍 \[*A*, *B*\) 中」表示由零或多個離散值組成、始於 *A* 終於 \(但不含\) *B* 的序列。  只有在可從 *A* 聯繫到 *B* 時，範圍才有效；您可以將 *A* 儲存在物件 *N* 中 \(*N* \= *A*\)、將物件增量零或多次 \(\+\+*N*\)，以及在增量有限次數 \(N \=\= B*\)* 後讓物件比較等於 *B*。  
  
-   片語「範圍 \[*A*, *B*\) 中的每個 *N*」表示 *N* 會從值 *A* 開始，並增量零或多次直到等於值 *B* 為止。  案例 *N* \=\= *B* 不在範圍內。  
  
-   片語「在 *X* 條件下，範圍 \[*A*, *B*\) 中的最小 *N* 值」表示會為範圍 \[*A*, *B*\) 中的每個 *N* 指定條件 *X*，直到符合條件 *X* 為止。  
  
-   片語「在 *X* 條件下，範圍 \[*A*, *B*\) 中的最大 *N* 值」表示會為範圍 \[*A*, *B*\) 中的每個 *N* 指定 *X*。  函式會在每次符合條件 *X* 時，在 `K` 中儲存 *N* 的複本。  執行任何此類儲存時，函式會將 *N* 的最終值 \(等於 *B*\) 取代為 `K` 的值。  但就雙向或隨機存取迭代器而言，這也可能表示 *N* 以範圍內的最大值開頭，然後在範圍內減量直到符合條件 *X* 為止。  
  
-   運算式，例如 *X* \- *Y*，其中 *X* 和 *Y* 可以是隨機存取迭代器以外的迭代器，用於數學領域。  函式在必須判斷這類值時不一定會評估 operator**\-**。  這同樣也適用於 *X* \+ *N* 和 *X* \- *N* 之類的運算式，其中 *N* 是整數類型。  
  
 有數種演算法使用會執行 pairwise 比較 \(例如與 `operator==`\) 的述詞來產生 `bool` 結果。  述詞函式 `operator==` \(或任何替代項目\) 不可變更其任一運算元。  它在每次評估時必須產生相同的 `bool` 結果，且在以其中一個運算元的複本替代運算元時必須產生相同結果。  
  
 有數個演算法使用必須對序列中的元素配對強制執行嚴格弱式順序的述詞。  就述詞 `pr`\(*X*, *Y*\) 而言：  
  
-   嚴格表示 `pr`\(*X*, *X*\) 為 false。  
  
-   弱式表示若 \!`pr`\(*X*, *Y*\) && \!`pr`\(*Y*, *X*\)，則 *X* 和 *Y* 具有相同排序 \(不需要定義 *X* \=\= *Y*\)。  
  
-   排序表示 `pr`\(*X*, *Y*\) && `pr`\(*Y*, Z\) 意指 `pr`\(*X*, Z\)。  
  
 其中有部分演算法會隱含地使用述詞 *X* \< *Y*。  其他通常符合嚴格弱式排序需求的述詞包括 *X* \> *Y*、**less**\(*X*, *Y*\) 和 `greater`\(*X*, *Y*\)。  但請注意，*X* \< \= *Y* 和 *X* \> \= *Y* 之類的述詞並不符合此需求。  
  
 迭代器在範圍 \[`First`, `Last`\) 中指定的元素序列，會是依 operator**\<** 排序的序列，前提是，對於範圍 \[0, `Last` \- `First`\) 中的每個 N 和範圍 \(N, `Last` \- `First`\) 中的每個 M，述詞 \!\(\*\(`First` \+ *M*\) \< \*\(*First* \+ *N*\)\) 為 true。  \(請注意，元素會以遞增順序排序\)。 述詞函式 **operator\<** \(或任何替代項目\) 不可變更其任一運算元。  它在每次評估時必須產生相同的 `bool` 結果，且在以其中一個運算元的複本替代運算元時必須產生相同結果。  此外，它必須對它所比較的運算元強制執行嚴格弱式排序。  
  
 迭代器在範圍 \[`First`, `Last`\) 中指定的元素序列，會是依 **operator\<** 排序的堆積，前提是，對於範圍 \[1, `Last` \- `First`\) 中的每個 N，述詞 \!\(\*`First` \< \*\(`First` \+ *N*\)\) 為 true。  \(第一個元素最大。\) 否則，將只有範本函式 [make\_heap](../Topic/make_heap.md)、[pop\_heap](../Topic/pop_heap.md) 和 [push\_heap](../Topic/push_heap.md) 可辨識其內部結構。  與排序順序相同，述詞函式 **operator\<** \(或任何替代項目\) 不可變更其任一運算元，且必須對它所比較的運算元強制執行嚴格弱式排序。  它在每次評估時必須產生相同的 `bool` 結果，且在以其中一個運算元的複本替代運算元時必須產生相同結果。  
  
 STL 演算法位於 [\<algorithm\>](../standard-library/algorithm.md) 和 [\<numeric\>](../standard-library/numeric.md) 標頭檔中。  
  
## 請參閱  
 [標準樣板程式庫](../misc/standard-template-library.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)