---
title: "&lt;algorithm&gt; | Microsoft Docs"
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
  - "<algorithm>"
  - "std::<algorithm>"
  - "algorithm/std::<algorithm>"
  - "std.<algorithm>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<algorithm> 標頭"
  - "algorithm 標頭 [C++]"
  - "Standard C++ 程式庫, 演算法"
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
caps.latest.revision: 23
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;algorithm&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義執行演算法的標準範本庫 \(STL\) 容器樣板函式。  
  
## 語法  
  
```  
(see relevant links below for specific algorithm syntax)  
```  
  
## 備註  
 因為它們可以在各種資料結構上作業，STL 演算法是泛型。  它們可以作業的資料結構不僅包含 STL 容器類別 \(例如 `vector` 和 `list`\)，還包含滿足特定演算法需求的程式定義資料結構和元素陣列。  STL 演算法間接透過迭代器存取和周遊容器的項目，來達成這個一般性層級。  
  
 STL 演算法處理迭代器範圍 \(通常由其開始或結束位置指定\)。  參考的範圍必須是有效的，這表示在範圍內的所有指標必須都是可取值，而且在每個範圍的序列中，最後一個位置必須可透過遞增從第一個位置連接。  
  
 STL 演算法擴充每一個 STL 容器的作業和成員函式所支援的動作，而且例如允許同時與不同類型的容器物件搭配使用。  兩個後置詞用來傳達演算法用途的相關資訊。  
  
-   `_if` 後置詞表示演算法是與在元素值上運算的函式物件搭配使用，而不是元素值本身。  `find_if` 演算法尋找值符合函式物件指定之準則的項目，而 `find` 演算法則搜尋特定值。  
  
-   \_copy 後置詞表示演算法不僅操作項目的值，還將修改後值複製到目的範圍。  `reverse` 演算法反轉範圍內項目的順序，而 `reverse_copy` 演算法也會將結果複製到目的範圍。  
  
 STL 演算法通常分類為表示其目的或需求的相關群組。  其中包括變更元素值的修改演算法，相較於不變更元素值的非修改演算法。  變動演算法變更項目的順序，但不變更項目的值。  移除演算法可以從範圍或範圍的複本排除項目。  排序演算法以各種方式重新排列範圍中的項目，而已排序範圍演算法只在已經透過特定方式排序項目的演算法上作用。  
  
 為數值處理提供的 STL 數值演算法有自己的標頭檔 [\<numeric\>](../standard-library/numeric.md)，而函式物件和配接器是在標頭 [\<functional\>](../standard-library/functional.md) 中定義。傳回布林值的函式物件稱為述詞。  預設二元述詞是比較 `operator<`。  通常，排序的項目必須是小於比較，因此若提供了兩個項目，可以判斷它們相等 \(任一個都不小於另一個的意義\)，或者一個小於另一個。  這會導致在非對等元件中的排序。  
  
### 函式  
  
|||  
|-|-|  
|[adjacent\_find](../Topic/adjacent_find.md)|搜尋等於或符合指定之條件的兩個相鄰項目。|  
|[all\_of](../Topic/all_of.md)|當條件出現在指定的範圍中的每個項目時，傳回 `true`。|  
|[any\_of](../Topic/any_of.md)|當條件出現在指定的項目範圍至少一次時，傳回 `true`。|  
|[binary\_search](../Topic/binary_search.md)|測試已排序的範圍中是否有等於指定之值 \(或在二元述詞指定的意義上，相當於該值\) 的項目。|  
|[copy](../Topic/copy.md)|從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以正向方向指派它們新位置。|  
|[copy\_backward](../Topic/copy_backward.md)|從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以反向方向指派它們新位置。|  
|[copy\_if](../Topic/copy_if.md)|複製特定範圍中針對指定的條件測試為 `true` 的所有項目|  
|[copy\_n](../Topic/copy_n.md)|複製指定的項目數目。|  
|[count](../Topic/count.md)|傳回範圍中值符合指定值的項目數目。|  
|[count\_if](../Topic/count_if.md)|傳回範圍中值符合指定條件的項目數目。|  
|[equal](../Topic/equal.md)|逐一比較兩個範圍的每個項目是否相等 \(或在二元述詞指定的意義上，是否對等\)。|  
|[equal\_range](../Topic/equal_range.md)|在已排序的範圍中尋找一對位置，第一個位置小於或等於指定項目的位置，第二個位置大於該項目的位置，其中用於建立序列中位置的等價或順序意義可由二元述詞指定。|  
|[fill](../Topic/fill.md)|將相同的新值指派到指定範圍內的每個項目。|  
|[fill\_n](../Topic/fill_n.md)|指派新值給範圍中以特定項目開頭的指定項目數。|  
|[find](../Topic/find%20\(STL\).md)|在範圍中找出有指定值的第一個項目的位置。|  
|[find\_end](../Topic/find_end.md)|在範圍中尋找與指定序列相同 \(或在二元述詞指定的意義上，相當於該序列\) 的最後一個子序列。|  
|[find\_first\_of](../Topic/find_first_of.md)|在目標範圍內搜尋第一次出現的任何多個值，或第一次出現的任何多個項目 \(在二元述詞指定的意義上，相當於指定之項目集合\)。|  
|[find\_if](../Topic/find_if.md)|在範圍中找出滿足特定條件的第一個項目的位置。|  
|[find\_if\_not](../Topic/find_if_not.md)|傳回指定範圍中不滿足條件的第一個項目。|  
|[for\_each](../Topic/for_each.md)|將指定的函式物件以正向順序套用至範圍內的每個項目，並傳回函式物件。|  
|[generate](../Topic/generate.md)|將函式物件產生的值指派給範圍內的每個項目。|  
|[generate\_n](../Topic/generate_n.md)|將函式物件產生的值指派給範圍內的指定項目數，並返回到超過最後一個指定值的位置。|  
|[includes](../Topic/includes.md)|測試一個排序範圍是否包含第二個排序範圍內的所有項目，其中項目之間的順序或等價準則可由二元述詞指定。|  
|[inplace\_merge](../Topic/inplace_merge.md)|將兩個連續排序範圍內的項目結合成單一排序範圍，其中順序準則可由二元述詞指定。|  
|[is\_heap](../Topic/is_heap.md)|如果在指定範圍內的項目形成堆積，則傳回 `true`。|  
|[is\_heap\_until](../Topic/is_heap_until.md)|如果指定的範圍形成堆積直到最後項目，則傳回 `true`。|  
|[is\_partitioned](../Topic/is_partitioned.md)|如果在指定範圍內針對條件測試為 `true` 的所有項目都是在測試為 `false` 的任何項目之前，傳回 `true`。|  
|[is\_permutation](../Topic/is_permutation.md)|判斷指定的範圍中的元素是否構成有效的排列。|  
|[is\_sorted](../Topic/is_sorted.md)|如果在指定範圍內的項目為已排序順序，則傳回 `true`。|  
|[is\_sorted\_until](../Topic/is_sorted_until.md)|如果在指定範圍內的項目為已排序順序，則傳回 `true`。|  
|[iter\_swap](../Topic/iter_swap.md)|交換由一組指定之迭代器所參考的兩個值。|  
|[lexicographical\_compare](../Topic/lexicographical_compare.md)|逐一比較兩個序列之間的每個項目，判斷兩者較小者。|  
|[lower\_bound](../Topic/lower_bound.md)|在已排序範圍中尋找值大於或相當於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。|  
|[make\_heap](../Topic/make_heap.md)|將在指定範圍內的項目轉換為堆積，其中第一個項目是最大，而且排序準則可由二元述詞指定。|  
|[max](../Topic/max.md)|比較兩個物件並傳回兩者較大者，其中順序準則可由二元述詞指定。|  
|[max\_element](../Topic/max_element.md)|在指定的範圍內尋找第一個最大項目，其中順序準則可由二元述詞指定。|  
|[merge](../Topic/merge.md)|將兩個排序來源範圍內的所有項目結合成單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[min](../Topic/min.md)|比較兩個物件並傳回兩者較小者，其中順序準則可由二元述詞指定。|  
|[min\_element](../Topic/min_element.md)|在指定的範圍內尋找第一個最小項目，其中順序準則可由二元述詞指定。|  
|[minmax](../Topic/minmax.md)|比較兩個輸入參數並做為一組傳回，從最小排到最大。|  
|[minmax\_element](../Topic/minmax_element.md)|在一個呼叫中執行 [min\_element](../Topic/min_element.md) 和 [max\_element](../Topic/max_element.md) 所執行的工作。|  
|[mismatch](../Topic/mismatch.md)|逐一比較兩個範圍的每個項目是否相等 \(或在二元述詞指定的意義上，是否對等\)，而且找出差異發生的第一個位置。|  
|[移動](../Topic/%3Calg%3E%20move.md)|移動與所指定範圍相關聯的項目。|  
|[move\_backward](../Topic/move_backward.md)|將一個迭代器的項目移至另一個迭代器。  從指定範圍內的最後一個項目開始移動，並以該範圍內的第一個項目結束。|  
|[next\_permutation](../Topic/next_permutation.md)|重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 \(如果有的話\)，其中下一個的意義可由二元述詞指定。|  
|[none\_of](../Topic/none_of.md)|當條件從未出現在指定的範圍中的項目時，傳回 `true`。|  
|[nth\_element](../Topic/nth_element.md)|分割項目的範圍，將序列的第 *n* 個項目正確放在範圍中，以便在它前面的所有項目小於或等於它，而且序列中在它後面的所有項目大於或等於它。|  
|[partial\_sort](../Topic/partial_sort.md)|將範圍中指定的較小項目數目排列成非遞減排列，或是依據二元述詞指定的順序準則。|  
|[partial\_sort\_copy](../Topic/partial_sort_copy.md)|從來源範圍將項目複製到目的範圍，其中來源項目是依小於排序，或依據二元述詞指定的順序準則。|  
|[partition](../Topic/partition.md)|將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前。|  
|[partition\_copy](../Topic/partition_copy.md)|將條件是 `true` 的項目複製到一個目的地，並將條件是 `false` 的項目複製到另一個目的地。  項目必須來自指定的範圍。|  
|[partition\_point](../Topic/partition_point.md)|傳回給定範圍中不滿足條件的第一個項目。  排序項目，以便滿足條件的項目在不滿足條件的項目之前。|  
|[pop\_heap](../Topic/pop_heap.md)|從堆積的前面移動最大的項目至範圍的倒數第二個位置，然後從其餘項目形成新的堆積。|  
|[prev\_permutation](../Topic/prev_permutation.md)|重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 \(如果有的話\)，其中下一個的意義可由二元述詞指定。|  
|[push\_heap](../Topic/push_heap.md)|將在範圍結尾的項目加入至由範圍中之前項目所組成的現有堆積。|  
|[random\_shuffle](../Topic/random_shuffle.md)|將範圍中 *N* 個項目的序列重新整理為 *N*\!  排列方式隨機選取的其中一個。|  
|[remove](../Topic/remove.md)|從指定範圍中排除指定的值，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。|  
|[remove\_copy](../Topic/remove_copy.md)|從來源範圍將項目複製到目的範圍，不過不會複製一個指定值的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。|  
|[remove\_copy\_if](../Topic/remove_copy_if.md)|從來源範圍將項目複製到目的範圍，不過不會複製滿足述詞的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。|  
|[remove\_if](../Topic/remove_if.md)|從指定範圍中排除滿足述詞的項目，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。|  
|[replace](../Topic/replace.md)|檢查範圍內的每個項目，如果符合指定的值則予以取代。|  
|[replace\_copy](../Topic/replace_copy.md)|檢查來源範圍內的每個項目，如果符合指定的值則予以取代，同時將結果複製到新目的範圍。|  
|[replace\_copy\_if](../Topic/replace_copy_if.md)|檢查來源範圍內的每個項目，如果滿足指定的述詞則予以取代，同時將結果複製到新目的範圍。|  
|[replace\_if](../Topic/replace_if.md)|檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。|  
|[reverse](../Topic/reverse.md)|反轉範圍內項目的順序。|  
|[reverse\_copy](../Topic/reverse_copy.md)|反轉來源範圍內項目的順序，並將其複製到目的範圍|  
|[rotate](../Topic/rotate.md)|交換兩個相鄰範圍的項目。|  
|[rotate\_copy](../Topic/rotate_copy.md)|交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。|  
|[search](../Topic/search.md)|在目標範圍中搜尋第一個序列，其項目等於指定項目序列中的項目，或在二元述詞指定的意義上，其項目相當於指定序列中的項目。|  
|[search\_n](../Topic/search_n.md)|在範圍中搜尋包含指定項目數的第一個子序列，這些項目具有特定值或在二元述詞指定的意義上與該值關聯。|  
|[set\_difference](../Topic/set_difference.md)|將屬於一個排序來源範圍但不屬於第二個排序來源範圍的所有項目聯集為單一排序的目的範圍，其中順序準則可由二元述詞指定。|  
|[set\_intersection](../Topic/set_intersection.md)|將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[set\_symmetric\_difference](../Topic/set_symmetric_difference.md)|將屬於兩個排序來源範圍之一 \(但非兩者\) 的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[set\_union](../Topic/set_union.md)|將至少屬於兩個排序來源範圍之一的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[sort](../Topic/sort.md)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則。|  
|[shuffle](../Topic/std::shuffle.md)|使用亂數產生器隨機播放 \(重新整理\) 指定範圍的項目。|  
|[sort\_heap](../Topic/sort_heap.md)|將堆積轉換為排序的範圍。|  
|[stable\_partition](../Topic/stable_partition.md)|將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前，保留對等項目的相對順序。|  
|[stable\_sort](../Topic/stable_sort.md)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則，並保留對等項目的相對順序。|  
|[交換](../Topic/swap.md)|在兩種類型的物件之間交換項目的值，將第一個物件的內容指派給第二個物件，並將第一個物件的內容指派給第一個物件。|  
|[swap\_ranges](../Topic/swap_ranges.md)|將某個範圍的項目與另一個相等大小之範圍的項目交換。|  
|[Transform \- 轉換](../Topic/transform.md)|將指定的函式物件應用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。|  
|[unique](../Topic/unique%20\(%3Calgorithm%3E\).md)|移除在指定範圍內彼此相鄰的重複項目。|  
|[unique\_copy](../Topic/unique_copy.md)|將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。|  
|[upper\_bound](../Topic/upper_bound.md)|在已排序範圍中尋找值大於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)