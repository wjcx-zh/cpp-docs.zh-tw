---
title: "演算法 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 5b5ffafb841fcb883dc66880933e8d123256e575
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="algorithms"></a>演算法
演算法是 C++ 標準程式庫的基礎部分。 演算法不會對容器本身執行，而是對迭代器執行。 因此，相同的演算法可供大部分甚至所有的 C++ 標準程式庫容器使用。 本節討論 C++ 標準程式庫演算法的慣例和術語。  
  
## <a name="remarks"></a>備註  
 在說明演算法範本函式時會使用數個速記片語：  
  
-   片語「在範圍 [*A*, *B*) 中」表示由零或多個離散值組成、始於 *A* 但結束於 (不含) *B* 的序列。只有在可從 *A* 聯繫到 *B* 時，範圍才有效；您可以將 *A* 儲存在物件 *N* 中 (*N* = *A*)、將物件增量零或多次 (++*N*)，以及在增量有限次數 (N == B) 後讓物件比較等於 *B*。  
  
-   片語「範圍 [*A*, *B*) 中的每個 *N*」表示 *N* 會從值 *A* 開始，並增量零或多次直到等於值 *B* 為止。案例 *N* == *B* 不在範圍內。  
  
-   片語「在 *X* 條件下，範圍 [*A*, *B*) 中的最小 *N* 值」表示會為範圍 [*A*, *B*) 中的每個 *N* 指定條件 *X*，直到符合條件 *X* 為止。  
  
-   片語「在 *X* 條件下，範圍 [*A*, *B*) 中的最大 *N* 值」表示會為範圍 [*A*, *B*) 中的每個 *N* 指定 *X*。 函式會在每次符合條件 *X* 時，在 `K` 中儲存 *N* 的複本。 執行任何這類儲存時，函式會將 *N* 的最終值 (等於 *B*) 取代為 `K` 的值。 但就雙向或隨機存取迭代器而言，這也可能表示 *N* 以範圍內的最大值開頭，然後在範圍內減量直到符合條件 *X* 為止。  
  
-   *X* - *Y* 這類運算式，其中 *X* 和 *Y* 可以是隨機存取迭代器以外的迭代器，用於數學領域。 函式在必須判斷這類值時不一定會評估 operator**-**。 這同樣也適用於 *X* + *N* 和 *X* - *N*，其中 *N* 是整數類型。  
  
 有數種演算法使用會執行 pairwise 比較 (例如與 `operator==`) 的述詞來產生 `bool` 結果。 述詞函式 `operator==` (或任何替代項目) 不可變更其任一運算元。 它在每次評估時必須產生相同的 `bool` 結果，且在以其中一個運算元的複本替代運算元時必須產生相同結果。  
  
 有數個演算法使用必須對序列中的元素配對強制執行嚴格弱式順序的述詞。 就述詞 `pr`(*X*, *Y*) 而言：  
  
-   嚴格表示 `pr`(*X*, *X*) 為 false。  
  
-   弱式表示若 !`pr`(*X*, *Y*) && !`pr`(*Y*, *X*)，則 *X* 和 *Y* 具有相同排序 (不需要定義 *X* == *Y*)。  
  
-   排序表示 `pr`(*X*, *Y*) && `pr`(*Y*, Z) 意指 `pr`(*X*, Z)。  
  
 其中有部分演算法會隱含地使用述詞 *X* \< *Y*。其他通常符合嚴格弱式排序需求的述詞包括 *X* > *Y*、**less**(*X*, *Y*) 和 `greater`(*X*, *Y*)。 但請注意，*X* \<= *Y* 和 *X* >= *Y* 之類的述詞並不符合此需求。  
  
 迭代器在範圍 [`First`, `Last`) 中指定的一序列元素，會是依 operator**<** 排序的序列，前提是，對於範圍 [0, `Last` - `First`) 中的每個 *N*，以及範圍 (N, `Last` - `First`) 中的每個 *M*，述詞 !(\*(`First` + *M*) < \*(*First* + *N*)) 為 true。 (請注意，元素會以遞增順序排序)。述詞函式 **operator<** (或任何替代項目) 不可變更其任一運算元。 它在每次評估時必須產生相同的 `bool` 結果，且在以其中一個運算元的複本替代運算元時必須產生相同結果。 此外，它必須對它所比較的運算元強制執行嚴格弱式排序。  
  
 迭代器在範圍 [`First`, `Last`) 中指定的一序列元素，會是依 **operator<** 排序的堆積，前提是，對於範圍 [1, `Last` - `First`) 中的每個 *N*述詞 !(\*`First` < \*(`First` + *N*)) 為 true。 (第一個元素最大。)只有範本函式 [make_heap](http://msdn.microsoft.com/Library/b09f795c-f368-4aa8-b57e-61ee6100ddc2)、[pop_heap]--brokenlink--(../Topic/not%20found:c10b0c65-410c-4c83-abf8-8b7f61bba8d0.md#pop_heap) 和 [push_heap]-brokenlink--(../Topic/not%20found:c10b0c65-410c-4c83-abf8-8b7f61bba8d0.md#push_heap) 才知道其內部結構。 與排序順序相同，述詞函式 **operator<** (或任何替代項目) 不可變更其任一運算元，且必須對它所比較的運算元強制執行嚴格弱式排序。 它在每次評估時必須產生相同的 `bool` 結果，且在以其中一個運算元的複本替代運算元時必須產生相同結果。  
  
 C++ 標準程式庫演算法位於 [\<algorithm>](../standard-library/algorithm.md) 和 [\<numeric>](../standard-library/numeric.md) 標頭檔中。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


