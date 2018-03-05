---
title: "演算法 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7dac0e574122342c96b28a2f5ccbeb1ea5088ae9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
定義 STL/CLR 容器樣板函式執行的演算法。  
  
## <a name="syntax"></a>語法  
  
```  
#include <cliext/algorithm>  
```  
  
## <a name="functions"></a>函式  
  
|功能|描述|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](../dotnet/adjacent-find-stl-clr.md)|搜尋兩個相鄰的項目相等。|  
|[binary_search (STL/CLR)](../dotnet/binary-search-stl-clr.md)|測試是否已排序的序列包含指定的值。|  
|[copy (STL/CLR)](../dotnet/copy-stl-clr.md)|將值從來源範圍複製到目的範圍，逐一查看正向方向。|  
|[copy_backward (STL/CLR)](../dotnet/copy-backward-stl-clr.md)|將值從來源範圍複製到目的範圍，逐一查看反向方向。|  
|[count (STL/CLR)](../dotnet/count-stl-clr.md)|傳回範圍中值符合指定值的項目數目。|  
|[count_if (STL/CLR)](../dotnet/count-if-stl-clr.md)|傳回範圍中值符合指定條件的項目數目。|  
|[equal (STL/CLR)](../dotnet/equal-stl-clr.md)|比較兩個範圍，逐一元件。|  
|[equal_range (STL/CLR)](../dotnet/equal-range-stl-clr.md)|搜尋值的排序的順序，並傳回兩個分隔的所有指定的項目相等的值序列的位置。|  
|[fill (STL/CLR)](../dotnet/fill-stl-clr.md)|將相同的新值指派到指定範圍內的每個項目。|  
|[fill_n (STL/CLR)](../dotnet/fill-n-stl-clr.md)|將新值指派給範圍中以特定元素開頭的指定元素數目。|  
|[find (STL/CLR)](../dotnet/find-stl-clr.md)|傳回指定值的第一次出現的位置。|  
|[find_end (STL/CLR)](../dotnet/find-end-stl-clr.md)|傳回與指定序列相同範圍中的最後一個子序列。|  
|[find_first_of (STL/CLR)](../dotnet/find-first-of-stl-clr.md)|搜尋第一個出現的任何一個指定的項目範圍的範圍。|  
|[find_if (STL/CLR)](../dotnet/find-if-stl-clr.md)|傳回值序列中第一個項目的位置，其中的項目符合指定的條件。|  
|[for_each (STL/CLR)](../dotnet/for-each-stl-clr.md)|適用於每個項目值序列中指定的函式物件，並傳回函式物件。|  
|[generate (STL/CLR)](../dotnet/generate-stl-clr.md)|指派給每個元素值序列中的函式物件產生的值。|  
|[generate_n (STL/CLR)](../dotnet/generate-n-stl-clr.md)|指派至指定的項目數函式物件產生的值。|  
|[includes (STL/CLR)](../dotnet/includes-stl-clr.md)|測試一個排序的範圍是否包含第二個排序範圍內的所有項目。|  
|[inplace_merge (STL/CLR)](../dotnet/inplace-merge-stl-clr.md)|將兩個連續排序範圍中的項目結合成單一排序範圍中。|  
|[iter_swap (STL/CLR)](../dotnet/iter-swap-stl-clr.md)|交換由一組指定之迭代器所參考的兩個值。|  
|[lexicographical_compare (STL/CLR)](../dotnet/lexicographical-compare-stl-clr.md)|比較兩個序列，這項，識別哪些順序兩個較小者。|  
|[lower_bound (STL/CLR)](../dotnet/lower-bound-stl-clr.md)|已排序序列中值的值大於或等於指定的值中尋找第一個項目的位置。|  
|[make_heap (STL/CLR)](../dotnet/make-heap-stl-clr.md)|將項目在指定範圍內轉換在堆積上的第一個元素的最大堆積。|  
|[max (STL/CLR)](../dotnet/max-stl-clr.md)|比較兩個物件，並傳回兩者的較大者。|  
|[max_element (STL/CLR)](../dotnet/max-element-stl-clr.md)|尋找最大的項目指定序列中的值。|  
|[merge (STL/CLR)](../dotnet/merge-stl-clr.md)|將兩個排序的來源範圍的所有項目結合成單一排序目的範圍。|  
|[min (STL/CLR)](../dotnet/min-stl-clr.md)|比較兩個物件，並傳回兩個較小者。|  
|[min_element (STL/CLR)](../dotnet/min-element-stl-clr.md)|尋找最小項目指定序列中的值。|  
|[mismatch (STL/CLR)](../dotnet/mismatch-stl-clr.md)|比較兩個範圍的項目並傳回差異發生的第一個位置。|  
|[next_permutation (STL/CLR)](../dotnet/next-permutation-stl-clr.md)|讓原始順序由語彙方面下一個更大的排列取代如果存在的話，請重新排列範圍中的項目。|  
|[nth_element (STL/CLR)](../dotnet/nth-element-stl-clr.md)|資料分割序列的項目正確放`n`序列 th 項目，使它前面的所有元素小於或等於它，而它後面的所有項目大於或等於它。|  
|[partial_sort (STL/CLR)](../dotnet/partial-sort-stl-clr.md)|指定的範圍中較小的項目數目排列成遞減順序。|  
|[partial_sort_copy (STL/CLR)](../dotnet/partial-sort-copy-stl-clr.md)|複製項目從來源範圍到目的範圍，來排序來源範圍中的項目。|  
|[partition (STL/CLR)](../dotnet/partition-stl-clr.md)|範圍中的項目排列，以便滿足一元述詞，這些項目之前，這滿足。|  
|[pop_heap (STL/CLR)](../dotnet/pop-heap-stl-clr.md)|然後 form 其餘項目從新的堆積和從堆積的前面移動最大的項目至結尾。|  
|[prev_permutation (STL/CLR)](../dotnet/prev-permutation-stl-clr.md)|讓原始順序由辭典編纂順序先前更大的排列取代如果存在的話，請重新排列項目序列。|  
|[push_heap (STL/CLR)](../dotnet/push-heap-stl-clr.md)|將在範圍結尾的項目加入至由範圍中之前項目所組成的現有堆積。|  
|[random_shuffle (STL/CLR)](../dotnet/random-shuffle-stl-clr.md)|重新排列一系列`N`的其中一個範圍中的項目`N`！ 排列方式隨機選取的其中一個。|  
|[remove (STL/CLR)](../dotnet/remove-stl-clr.md)|從指定範圍中刪除指定的值，而不會干擾其餘項目的順序，並傳回指定值的新範圍的結尾。|  
|[remove_copy (STL/CLR)](../dotnet/remove-copy-stl-clr.md)|項目從來源範圍複製到目的範圍，不同之處在於不複製一個指定值的項目，也不會干擾其餘項目的順序。|  
|[remove_copy_if (STL/CLR)](../dotnet/remove-copy-if-stl-clr.md)|複製項目從來源範圍到目的範圍，除了滿足述詞，也不會干擾其餘項目的順序。|  
|[remove_if (STL/CLR)](../dotnet/remove-if-stl-clr.md)|刪除滿足述詞，從指定範圍也不會干擾其餘項目的順序的項目。 。|  
|[replace (STL/CLR)](../dotnet/replace-stl-clr.md)|取代範圍中符合指定的值，以新值的項目。|  
|[replace_copy (STL/CLR)](../dotnet/replace-copy-stl-clr.md)|複製項目從來源範圍到目的範圍，取代符合指定的值，以新值的項目。|  
|[replace_copy_if (STL/CLR)](../dotnet/replace-copy-if-stl-clr.md)|檢查來源範圍內的每個項目，如果滿足指定的述詞則予以取代，同時將結果複製到新目的範圍。|  
|[replace_if (STL/CLR)](../dotnet/replace-if-stl-clr.md)|檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。|  
|[reverse (STL/CLR)](../dotnet/reverse-stl-clr.md)|反轉範圍內項目的順序。|  
|[reverse_copy (STL/CLR)](../dotnet/reverse-copy-stl-clr.md)|反轉來源範圍內項目的順序，將其複製到目的範圍。|  
|[rotate (STL/CLR)](../dotnet/rotate-stl-clr.md)|交換兩個相鄰範圍的項目。|  
|[rotate_copy (STL/CLR)](../dotnet/rotate-copy-stl-clr.md)|交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。|  
|[search (STL/CLR)](../dotnet/search-stl-clr.md)|在目標範圍中搜尋第一個序列，其項目等於指定項目序列中的項目，或在二元述詞指定的意義上，其項目相當於指定序列中的項目。|  
|[search_n (STL/CLR)](../dotnet/search-n-stl-clr.md)|在範圍中搜尋包含指定項目數的第一個子序列，這些項目具有特定值或在二元述詞指定的意義上與該值關聯。|  
|[set_difference (STL/CLR)](../dotnet/set-difference-stl-clr.md)|將屬於一個排序來源範圍但不屬於第二個排序來源範圍的所有項目聯集為單一排序的目的範圍，其中順序準則可由二元述詞指定。|  
|[set_intersection (STL/CLR)](../dotnet/set-intersection-stl-clr.md)|將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[set_symmetric_difference (STL/CLR)](../dotnet/set-symmetric-difference-stl-clr.md)|將屬於兩個排序來源範圍之一 (但非兩者) 的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[set_union (STL/CLR)](../dotnet/set-union-stl-clr.md)|將至少屬於兩個排序來源範圍之一的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[sort (STL/CLR)](../dotnet/sort-stl-clr.md)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則。|  
|[sort_heap (STL/CLR)](../dotnet/sort-heap-stl-clr.md)|將堆積轉換為排序的範圍。|  
|[stable_partition (STL/CLR)](../dotnet/stable-partition-stl-clr.md)|將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前，保留對等項目的相對順序。|  
|[stable_sort (STL/CLR)](../dotnet/stable-sort-stl-clr.md)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則，並保留對等項目的相對順序。|  
|[swap (STL/CLR)](../dotnet/swap-stl-clr.md)|在兩種類型的物件之間交換項目的值，將第一個物件的內容指派給第二個物件，並將第一個物件的內容指派給第一個物件。|  
|[swap_ranges (STL/CLR)](../dotnet/swap-ranges-stl-clr.md)|將某個範圍的項目與另一個相等大小之範圍的項目交換。|  
|[transform (STL/CLR)](../dotnet/transform-stl-clr.md)|將指定的函式物件應用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。|  
|[unique (STL/CLR)](../dotnet/unique-stl-clr.md)|移除在指定範圍內彼此相鄰的重複項目。|  
|[unique_copy (STL/CLR)](../dotnet/unique-copy-stl-clr.md)|將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。|  
|[upper_bound (STL/CLR)](../dotnet/upper-bound-stl-clr.md)|在已排序範圍中尋找值大於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。|  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)