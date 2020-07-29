---
title: '&lt;algorithm&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: a2a48eec2ed75fffd711a8704cb8c896f8ee7242
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205531"
---
# <a name="ltalgorithmgt"></a>&lt;algorithm&gt;

定義可執行演算法的 C++ 標準程式庫容器範本函式。

## <a name="syntax"></a>語法

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> 連結 \<algorithm> 庫也會使用 `#include <initializer_list>` 語句。

## <a name="remarks"></a>備註

C++ 標準程式庫演算法可以在各種資料結構上作業，因此為泛型。 它們可以作業的資料結構不僅包含 C++ 標準程式庫容器類別 (例如 `vector` 和 `list`)，還包含滿足特定演算法需求的程式定義資料結構和元素陣列。 C++ 標準程式庫演算法間接透過迭代器存取和周遊容器的元素，來達成這個一般性層級。

C++ 標準程式庫演算法會處理通常透過開始或結束位置指定的迭代器範圍。 參考的範圍必須是有效的，這表示在範圍內的所有指標必須都是可取值，而且在每個範圍的序列中，最後一個位置必須可透過遞增從第一個位置連接。

C++ 標準程式庫演算法會擴充每個 C++ 標準程式庫容器的作業和成員函式所支援的動作，而且例如允許同時與不同類型的容器物件搭配使用。 兩個後置詞用來傳達演算法用途的相關資訊。

- 後置詞 `_if` 表示演算法會與函式物件搭配使用，而不是在專案本身的值上運作。 `find_if` 演算法尋找值符合函式物件指定之準則的項目，而 `find` 演算法則搜尋特定值。

- _copy 後置詞表示演算法不僅操作項目的值，還將修改後值複製到目的範圍。 `reverse` 演算法反轉範圍內項目的順序，而 `reverse_copy` 演算法也會將結果複製到目的範圍。

C++ 標準程式庫演算法通常分類為表示其目的或需求的相關群組。 其中包括變更元素值的修改演算法，相較於不變更元素值的非修改演算法。 變動演算法變更項目的順序，但不變更項目的值。 移除演算法可以從範圍或範圍的複本排除項目。 排序演算法會以各種方式重新排列範圍中的元素，而已排序的範圍演算法只會對其專案以特定方式排序的範圍採取動作。

為數值處理提供的 c + + 標準程式庫數值演算法有自己的標頭檔 [\<numeric>](numeric.md) ，而函式物件和介面卡則定義于標頭函式 [\<functional>](functional.md) 物件中，而這些物件會傳回布林值，稱為述詞。 預設二元述詞是比較 `operator<`。 通常，排序的項目必須是小於比較，因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致在非對等元件中的排序。

### <a name="function-templates"></a>函式範本

|||
|-|-|
|[adjacent_find](algorithm-functions.md#adjacent_find)|搜尋等於或符合指定之條件的兩個相鄰項目。|
|[all_of](algorithm-functions.md#all_of)|**`true`** 當指定範圍內的每個專案都有條件時，會傳回。|
|[any_of](algorithm-functions.md#any_of)|**`true`** 當條件出現在指定的專案範圍內至少一次時，傳回。|
|[binary_search](algorithm-functions.md#binary_search)|測試已排序的範圍中是否有等於指定之值 (或在二元述詞指定的意義上，相當於該值) 的項目。|
|[夾具](algorithm-functions.md#clamp)||
|[copy](algorithm-functions.md#copy)|從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以正向方向指派它們新位置。|
|[copy_backward](algorithm-functions.md#copy_backward)|從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以反向方向指派它們新位置。|
|[copy_if](algorithm-functions.md#copy_if)|複製指定範圍中的所有專案，以測試 **`true`** 指定的條件|
|[copy_n](algorithm-functions.md#copy_n)|複製指定的項目數目。|
|[計數](algorithm-functions.md#count)|傳回範圍中值符合指定值的項目數目。|
|[count_if](algorithm-functions.md#count_if)|傳回範圍中值符合指定條件的項目數目。|
|[等於](algorithm-functions.md#equal)|逐一比較兩個範圍的每個項目是否相等 (或在二元述詞指定的意義上，是否對等)。|
|[equal_range](algorithm-functions.md#equal_range)|在已排序的範圍中尋找一對位置，第一個位置小於或等於指定項目的位置，第二個位置大於該項目的位置，其中用於建立序列中位置的等價或順序意義可由二元述詞指定。|
|[填滿](algorithm-functions.md#fill)|將相同的新值指派到指定範圍內的每個項目。|
|[fill_n](algorithm-functions.md#fill_n)|指派新值給範圍中以特定項目開頭的指定項目數。|
|[find](algorithm-functions.md#find)|在範圍中找出有指定值的第一個項目的位置。|
|[find_end](algorithm-functions.md#find_end)|在範圍中尋找與指定序列相同 (或在二元述詞指定的意義上，相當於該序列) 的最後一個子序列。|
|[find_first_of](algorithm-functions.md#find_first_of)|在目標範圍內搜尋第一次出現的任何多個值，或第一次出現的任何多個項目 (在二元述詞指定的意義上，相當於指定之項目集合)。|
|[find_if](algorithm-functions.md#find_if)|在範圍中找出滿足特定條件的第一個項目的位置。|
|[find_if_not](algorithm-functions.md#find_if_not)|傳回指定範圍中不滿足條件的第一個項目。|
|[for_each](algorithm-functions.md#for_each)|將指定的函式物件以正向順序套用至範圍內的每個項目，並傳回函式物件。|
|[for_each_n](algorithm-functions.md#for_each_n)||
|[創造](algorithm-functions.md#generate)|將函式物件產生的值指派給範圍內的每個項目。|
|[generate_n](algorithm-functions.md#generate_n)|將函式物件產生的值指派給範圍內的指定項目數，並返回到超過最後一個指定值的位置。|
|[包含](algorithm-functions.md#includes)|測試一個排序範圍是否包含第二個排序範圍內的所有項目，其中項目之間的順序或等價準則可由二元述詞指定。|
|[inplace_merge](algorithm-functions.md#inplace_merge)|將兩個連續排序範圍內的項目結合成單一排序範圍，其中順序準則可由二元述詞指定。|
|[is_heap](algorithm-functions.md#is_heap)|**`true`** 如果指定範圍內的元素形成堆積，則傳回。|
|[is_heap_until](algorithm-functions.md#is_heap_until)|**`true`** 如果指定的範圍形成堆積直到最後一個元素，則傳回。|
|[is_partitioned](algorithm-functions.md#is_partitioned)|**`true`** 如果指定範圍中測試條件的所有元素都在 **`true`** 測試的任何元素之前，則傳回 **`false`** 。|
|[is_permutation](algorithm-functions.md#is_permutation)|判斷指定的範圍中的元素是否構成有效的排列。|
|[is_sorted](algorithm-functions.md#is_sorted)|**`true`** 如果指定範圍內的專案為排序次序，則傳回。|
|[is_sorted_until](algorithm-functions.md#is_sorted_until)|**`true`** 如果指定範圍內的專案為排序次序，則傳回。|
|[iter_swap](algorithm-functions.md#iter_swap)|交換由一組指定之迭代器所參考的兩個值。|
|[lexicographical_compare](algorithm-functions.md#lexicographical_compare)|逐一比較兩個序列之間的每個項目，判斷兩者較小者。|
|[lower_bound](algorithm-functions.md#lower_bound)|在已排序範圍中尋找值大於或相當於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。|
|[make_heap](algorithm-functions.md#make_heap)|將在指定範圍內的項目轉換為堆積，其中第一個項目是最大，而且排序準則可由二元述詞指定。|
|[max](algorithm-functions.md#max)|比較兩個物件並傳回兩者較大者，其中順序準則可由二元述詞指定。|
|[max_element](algorithm-functions.md#max_element)|在指定的範圍內尋找第一個最大項目，其中順序準則可由二元述詞指定。|
|[合併](algorithm-functions.md#merge)|將兩個排序來源範圍內的所有項目結合成單一排序目的範圍，其中順序準則可由二元述詞指定。|
|[min](algorithm-functions.md#min)|比較兩個物件並傳回兩者較小者，其中順序準則可由二元述詞指定。|
|[min_element](algorithm-functions.md#min_element)|在指定的範圍內尋找第一個最小項目，其中順序準則可由二元述詞指定。|
|[minmax](algorithm-functions.md#minmax)|比較兩個輸入參數並做為一組傳回，從最小排到最大。|
|[minmax_element](algorithm-functions.md#minmax_element)|在一個呼叫中執行 [min_element](algorithm-functions.md#min_element) 和 [max_element](algorithm-functions.md#max_element) 所執行的工作。|
|[mismatch](algorithm-functions.md#mismatch)|逐一比較兩個範圍的每個項目是否相等 (或在二元述詞指定的意義上，是否對等)，而且找出差異發生的第一個位置。|
|[&lt;alg &gt; 移動](algorithm-functions.md#alg_move)|移動與所指定範圍相關聯的項目。|
|[move_backward](algorithm-functions.md#move_backward)|將一個迭代器的項目移至另一個迭代器。 從指定範圍內的最後一個項目開始移動，並以該範圍內的第一個項目結束。|
|[next_permutation](algorithm-functions.md#next_permutation)|重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 (如果有的話)，其中下一個的意義可由二元述詞指定。|
|[none_of](algorithm-functions.md#none_of)|**`true`** 當條件永遠不會出現在給定範圍中的專案之間時，會傳回。|
|[nth_element](algorithm-functions.md#nth_element)|分割某範圍的元素，將序列的第 *n* 個元素正確放入範圍中，以便在它前面的所有元素小於或等於它，而且序列中在它後面的所有元素大於或等於它。|
|[partial_sort](algorithm-functions.md#partial_sort)|將範圍中指定的較小項目數目排列成非遞減排列，或是依據二元述詞指定的順序準則。|
|[partial_sort_copy](algorithm-functions.md#partial_sort_copy)|從來源範圍將項目複製到目的範圍，其中來源項目是依小於排序，或依據二元述詞指定的順序準則。|
|[劃分](algorithm-functions.md#partition)|將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前。|
|[partition_copy](algorithm-functions.md#partition_copy)|將條件是的專案複製 **`true`** 到一個目的地，並將其條件設為另一個目的地 **`false`** 。 項目必須來自指定的範圍。|
|[partition_point](algorithm-functions.md#partition_point)|傳回給定範圍中不滿足條件的第一個項目。 排序項目，以便滿足條件的項目在不滿足條件的項目之前。|
|[pop_heap](algorithm-functions.md#pop_heap)|從堆積的前面移動最大的項目至範圍的倒數第二個位置，然後從其餘項目形成新的堆積。|
|[prev_permutation](algorithm-functions.md#prev_permutation)|重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 (如果有的話)，其中下一個的意義可由二元述詞指定。|
|[push_heap](algorithm-functions.md#push_heap)|將在範圍結尾的項目加入至由範圍中之前項目所組成的現有堆積。|
|[random_shuffle](algorithm-functions.md#random_shuffle)|將範圍中 *N* 個元素的序列重新整理為 *N*! 排列方式隨機選取的其中一個。|
|[remove](algorithm-functions.md#remove)|從指定範圍中排除指定的值，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。|
|[remove_copy](algorithm-functions.md#remove_copy)|從來源範圍將項目複製到目的範圍，不過不會複製一個指定值的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。|
|[remove_copy_if](algorithm-functions.md#remove_copy_if)|從來源範圍將項目複製到目的範圍，不過不會複製滿足述詞的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。|
|[remove_if](algorithm-functions.md#remove_if)|從指定範圍中排除滿足述詞的項目，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。|
|[replace](algorithm-functions.md#replace)|檢查範圍內的每個項目，如果符合指定的值則予以取代。|
|[replace_copy](algorithm-functions.md#replace_copy)|檢查來源範圍內的每個項目，如果符合指定的值則予以取代，同時將結果複製到新目的範圍。|
|[replace_copy_if](algorithm-functions.md#replace_copy_if)|檢查來源範圍內的每個項目，如果滿足指定的述詞則予以取代，同時將結果複製到新目的範圍。|
|[replace_if](algorithm-functions.md#replace_if)|檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。|
|[反向](algorithm-functions.md#reverse)|反轉範圍內項目的順序。|
|[reverse_copy](algorithm-functions.md#reverse_copy)|反轉來源範圍內項目的順序，並將其複製到目的範圍|
|[向](algorithm-functions.md#rotate)|交換兩個相鄰範圍的項目。|
|[rotate_copy](algorithm-functions.md#rotate_copy)|交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。|
|[抽樣](algorithm-functions.md#sample)||
|[search](algorithm-functions.md#search)|在目標範圍中搜尋第一個序列，其項目等於指定項目序列中的項目，或在二元述詞指定的意義上，其項目相當於指定序列中的項目。|
|[search_n](algorithm-functions.md#search_n)|在範圍中搜尋包含指定項目數的第一個子序列，這些項目具有特定值或在二元述詞指定的意義上與該值關聯。|
|[set_difference](algorithm-functions.md#set_difference)|將屬於一個排序來源範圍但不屬於第二個排序來源範圍的所有項目聯集為單一排序的目的範圍，其中順序準則可由二元述詞指定。|
|[set_intersection](algorithm-functions.md#set_intersection)|將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|
|[set_symmetric_difference](algorithm-functions.md#set_symmetric_difference)|將屬於兩個排序來源範圍之一 (但非兩者) 的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|
|[set_union](algorithm-functions.md#set_union)|將至少屬於兩個排序來源範圍之一的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|
|[sort](algorithm-functions.md#sort)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則。|
|[隨機播放](algorithm-functions.md#shuffle)|使用亂數產生器隨機播放 (重新整理) 指定範圍的項目。|
|[sort_heap](algorithm-functions.md#sort_heap)|將堆積轉換為排序的範圍。|
|[stable_partition](algorithm-functions.md#stable_partition)|將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前，保留對等項目的相對順序。|
|[stable_sort](algorithm-functions.md#stable_sort)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則，並保留對等項目的相對順序。|
|[調換](algorithm-functions.md#swap)|在兩種類型的物件之間交換項目的值，將第一個物件的內容指派給第二個物件，並將第一個物件的內容指派給第一個物件。|
|[swap_ranges](algorithm-functions.md#swap_ranges)|將某個範圍的項目與另一個相等大小之範圍的項目交換。|
|[轉換](algorithm-functions.md#transform)|將指定的函式物件應用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。|
|[unique](algorithm-functions.md#unique)|移除在指定範圍內彼此相鄰的重複項目。|
|[unique_copy](algorithm-functions.md#unique_copy)|將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。|
|[upper_bound](algorithm-functions.md#upper_bound)|在已排序範圍中尋找值大於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](cpp-standard-library-reference.md)
