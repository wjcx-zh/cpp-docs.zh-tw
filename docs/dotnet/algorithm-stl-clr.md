---
title: "algorithm (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/algorithm>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<algorithm> 標頭 [STL/CLR]"
  - "<cliext/algorithm> 標頭 [STL/CLR]"
  - "algorithm 函式 [STL/CLR]"
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# algorithm (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 STL\/CLR 容器樣板函式執行演算法。  
  
## 語法  
  
```  
#include <cliext/algorithm>  
```  
  
## 函式  
  
|功能|說明|  
|--------|--------|  
|[adjacent\_find](../dotnet/adjacent-find-stl-clr.md)|搜尋是相等的兩個相鄰的項目。|  
|[binary\_search](../dotnet/binary-search-stl-clr.md)|測試的排序序列是否包含特定值。|  
|[copy](../dotnet/copy-stl-clr.md)|從一個來源範圍的值複製到目的陣列，逐一查看正向。|  
|[copy\_backward](../dotnet/copy-backward-stl-clr.md)|從一個來源範圍的值複製到目的陣列，逐一查看這個反向。|  
|[count](../dotnet/count-stl-clr.md)|傳回項目數的值符合指定的範圍。|  
|[count\_if](../dotnet/count-if-stl-clr.md)|傳回項目數的值符合指定條件的範圍。|  
|[equal](../dotnet/equal-stl-clr.md)|比較兩個範圍，由項目的項目。|  
|[equal\_range](../dotnet/equal-range-stl-clr.md)|搜尋值序列並傳回分隔值 subsequence 是所有等於某個項目的兩個位置。|  
|[填滿](../dotnet/fill-stl-clr.md)|指派相同的新值對中指定範圍內的每個項目。|  
|[fill\_n](../dotnet/fill-n-stl-clr.md)|指派新值給以特定項目開頭之範圍中的指定項目數。|  
|[尋找](../dotnet/find-stl-clr.md)|傳回指定值的第一個項目的位置。|  
|[find\_end](../dotnet/find-end-stl-clr.md)|傳回具有指定之序列相同範圍中的最後一個 subsequence。|  
|[find\_first\_of](../dotnet/find-first-of-stl-clr.md)|搜尋一個範圍中第一個符合任何一個項目的指定範圍。|  
|[find\_if](../dotnet/find-if-stl-clr.md)|傳回第一個項目位置在項目中符合指定之條件的值序列。|  
|[for\_each](../dotnet/for-each-stl-clr.md)|套用至每個項目的指定函式物件在值序列並傳回函式物件。|  
|[產生](../dotnet/generate-stl-clr.md)|指派給每個項目的函式物件產生的值。值序列。|  
|[generate\_n](../dotnet/generate-n-stl-clr.md)|指派給項目的指定數目的函式物件產生的值。|  
|[includes](../dotnet/includes-stl-clr.md)|測試一個人員是否排序範圍包含在第二個排序範圍內的所有項目。|  
|[inplace\_merge](../dotnet/inplace-merge-stl-clr.md)|合併兩個連續排序範圍內的元素至單一排序的範圍。|  
|[iter\_swap](../dotnet/iter-swap-stl-clr.md)|交換兩個值由一組指定之 Iterator 所參考的。|  
|[lexicographical\_compare](../dotnet/lexicographical-compare-stl-clr.md)|比較兩個序列，由序列是較小的兩個元素的元素，識別。|  
|[lower\_bound](../dotnet/lower-bound-stl-clr.md)|尋找第一個項目位置有值大於或等於指定值的值的序列。|  
|[make\_heap](../dotnet/make-heap-stl-clr.md)|轉換從指定範圍中的項目在堆積中的第一個項目是最大的堆積。|  
|[max](../dotnet/max-stl-clr.md)|比較兩個物件並傳回大兩個。|  
|[max\_element](../dotnet/max-element-stl-clr.md)|尋找在值所指定的最大項目。|  
|[合併](../dotnet/merge-stl-clr.md)|合併兩個排序的來源範圍的所有項目至單一，排序的目的範圍。|  
|[min](../dotnet/min-stl-clr.md)|比較兩個物件並傳回較小者兩者。|  
|[min\_element](../dotnet/min-element-stl-clr.md)|尋找在值所指定的最小的項目。|  
|[mismatch](../dotnet/mismatch-stl-clr.md)|由項目比較兩個範圍的項目並傳回差異發生的第一個位置。|  
|[next\_permutation](../dotnet/next-permutation-stl-clr.md)|若要重新排列範圍的項目，讓原始順序由詞傳統的下一個較大的範圍取代，如果有的話。|  
|[nth\_element](../dotnet/nth-element-stl-clr.md)|分割，正確設定序列的 `n`th 項目序列，以便在它前面的所有項目小於或等於，而且後面的所有項目大於或等於它。|  
|[partial\_sort](../dotnet/partial-sort-stl-clr.md)|排列較小的項目中所指定的數字範圍中輸入 nondescending 的命令。|  
|[partial\_sort\_copy](../dotnet/partial-sort-copy-stl-clr.md)|複製來源範圍的項目到目的範圍這類從來源範圍的項目已排序。|  
|[partition](../dotnet/partition-stl-clr.md)|軸範圍中的項目這類滿足一元的述詞的項目在不符合其那些之前。|  
|[pop\_heap](../dotnet/pop-heap-stl-clr.md)|從堆積的前面移動的最大項目移動至結束然後形成從其餘項目的新的堆積。|  
|[prev\_permutation](../dotnet/prev-permutation-stl-clr.md)|重新排列項目序列，讓原始順序由詞傳統的上一個更大的範圍取代，如果有的話。|  
|[push\_heap](../dotnet/push-heap-stl-clr.md)|將會在範圍的結尾為包含範圍中現有的堆積前置的項目。|  
|[random\_shuffle](../dotnet/random-shuffle-stl-clr.md)|重新排列 `N` 項目序列範圍中的其中一個 `N`\!隨機選取的排列方式。|  
|[移除](../dotnet/remove-stl-clr.md)|刪除從指定範圍中的值，而不會干擾其他元素順序並傳回新的範圍結尾沒有指定值。|  
|[remove\_copy](../dotnet/remove-copy-stl-clr.md)|複製來源範圍的項目到目的範圍，不過，一個指定值的項目不會複製，不會干擾其他項目的順序。|  
|[remove\_copy\_if](../dotnet/remove-copy-if-stl-clr.md)|複製來源範圍的項目加入至目的範圍，除了滿足述詞的項目，而不會干擾，其餘項目的順序。|  
|[remove\_if](../dotnet/remove-if-stl-clr.md)|刪除滿足從指定範圍的述詞，而不會干擾其他元素順序的項目。.|  
|[取代](../dotnet/replace-stl-clr.md)|取代符合指定值為新的值範圍內的元素。|  
|[replace\_copy](../dotnet/replace-copy-stl-clr.md)|複製來源範圍的項目到目的範圍，取代符合指定值以新值的元素。|  
|[replace\_copy\_if](../dotnet/replace-copy-if-stl-clr.md)|檢查來源範圍的每個項目並取代它，則滿足指定的述詞，當複製結果載入至新的範圍。|  
|[replace\_if](../dotnet/replace-if-stl-clr.md)|如果滿足指定的述詞，檢查在範圍內的每個項目並取代它。|  
|[reverse](../dotnet/reverse-stl-clr.md)|反轉項目的順序在範圍內。|  
|[reverse\_copy](../dotnet/reverse-copy-stl-clr.md)|反轉項目的順序指定來源的，並將其複製到目的範圍時。|  
|[rotate](../dotnet/rotate-stl-clr.md)|若要在兩個相鄰範圍的項目。|  
|[rotate\_copy](../dotnet/rotate-copy-stl-clr.md)|若要在兩個相鄰範圍內的元素指定來源並複製結果到目的範圍。|  
|[search](../dotnet/search-stl-clr.md)|查詢類似序列中的第一個二進位述詞實際上就相當於指定的項目與相等項目指定序列或項目與項目在指定序列的目標範圍內。|  
|[search\_n](../dotnet/search-n-stl-clr.md)|搜尋項目指定的數字具有特定的值或與該值依二進位述詞的範圍的第一 subsequence。|  
|[set\_difference](../dotnet/set-difference-stl-clr.md)|聯集屬於一個排序的來源範圍的所有項目，但是，對第二個排序來源範圍，到單一，排序的目的範圍，排序準則可能由二進位述詞指定。|  
|[set\_intersection](../dotnet/set-intersection-stl-clr.md)|聯集屬於兩個排序的來源範圍成單一的所有項目，排序的目的範圍，排序準則可能由二進位述詞指定。|  
|[set\_symmetric\_difference](../dotnet/set-symmetric-difference-stl-clr.md)|聯集屬於其中一個的所有項目，但是，但不能同時指定兩者，排序的來源範圍到單一裡，排序目的範圍，排序準則可能由二進位述詞指定。|  
|[set\_union](../dotnet/set-union-stl-clr.md)|聯集屬於兩個排序的來源範圍至少有一個輸入唯一的所有項目，排序的目的範圍，排序準則可能由二進位述詞指定。|  
|[排序](../dotnet/sort-stl-clr.md)|表示在指定範圍內的元素載入至 nondescending 的命令或以二進位述詞指定的排序準則。|  
|[sort\_heap](../dotnet/sort-heap-stl-clr.md)|轉換堆積至排序的範圍。|  
|[stable\_partition](../dotnet/stable-partition-stl-clr.md)|分類在範圍中之項目的兩個互斥集，而這些項目符合不符合其那些之前的一元的述詞，保留相等項目的相對順序。|  
|[stable\_sort](../dotnet/stable-sort-stl-clr.md)|表示在指定範圍內的元素載入至 nondescending 的命令或以二進位述詞指定的排序準則並保留相等項目的相對順序。|  
|[swap](../dotnet/swap-stl-clr.md)|切換項目的值在物件之間有兩種類型的，將第一個物件加入至物件內容和內容對話方塊的第一個。|  
|[swap\_ranges](../dotnet/swap-ranges-stl-clr.md)|交換某個範圍的項目與其他項目相等，大小的範圍。|  
|[transform](../dotnet/transform-stl-clr.md)|將指定的函式物件至來源中的每個項目或對一組從兩個來源範圍的元素複製到函式物件的傳回值到目的範圍。|  
|[唯一](../dotnet/unique-stl-clr.md)|移除是彼此相鄰中指定範圍內的重複的項目。|  
|[unique\_copy](../dotnet/unique-copy-stl-clr.md)|複製來源範圍的項目到目的範圍除了是彼此相鄰的重複的項目。|  
|[upper\_bound](../dotnet/upper-bound-stl-clr.md)|在包含的值大於指定值的已排序範圍中尋找第一個項目的位置，其中排序準則可藉由二元述詞指定。|  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [STL\/CLR 程式庫](../dotnet/stl-clr-library-reference.md)