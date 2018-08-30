---
title: 演算法 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
dev_langs:
- C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 93bbc86e32d75e81c342a0a0a71b823b87df62b0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196761"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
定義 STL/CLR 容器樣板函式可執行演算法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
#include <cliext/algorithm>  
```  

## <a name="requirements"></a>需求  
 **標頭：** \<cliext/演算法 >  
  
 **命名空間：** cliext  
    
## <a name="declarations"></a>宣告  
  
|函式|描述|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](#adjacent_find)|搜尋兩個相鄰的項目相等。|  
|[binary_search (STL/CLR)](#binary_search)|測試是否已排序的序列包含指定的值。|  
|[copy (STL/CLR)](#copy)|將值從來源範圍複製到目的範圍，在 正向方向逐一查看。|  
|[copy_backward (STL/CLR)](#copy_backward)|將值從來源範圍複製到目的範圍，向後逐一查看。|  
|[count (STL/CLR)](#count)|傳回範圍中值符合指定值的項目數目。|  
|[count_if (STL/CLR)](#count_if)|傳回範圍中值符合指定條件的項目數目。|  
|[equal (STL/CLR)](#equal)|比較兩個範圍，藉由項目。|  
|[equal_range (STL/CLR)](#equal_range)|搜尋已排序的值，並傳回兩個位置，用來分隔的值，指定的項目完全相同的子序列。|  
|[fill (STL/CLR)](#fill)|將相同的新值指派到指定範圍內的每個項目。|  
|[fill_n (STL/CLR)](#fill_n)|將新值指派給範圍中以特定元素開頭的指定元素數目。|  
|[find (STL/CLR)](#find)|傳回指定之值的第一次出現的位置。|  
|[find_end (STL/CLR)](#find_end)|傳回等同於指定的順序的範圍中的最後一個子序列。|  
|[find_first_of (STL/CLR)](#find_first_of)|搜尋範圍，以第一個出現的任何一個指定之範圍的項目。|  
|[find_if (STL/CLR)](#find_if)|傳回第一個元素的位置值序列中項目符合指定的條件的位置。|  
|[for_each (STL/CLR)](#for_each)|套用指定的函式物件之值序列中的每個項目，並傳回的函式物件。|  
|[generate (STL/CLR)](#generate)|會指派每個元素值序列中的函式物件所產生的值。|  
|[generate_n (STL/CLR)](#generate_n)|指派至指定的元素數目的函式物件所產生的值。|  
|[includes (STL/CLR)](#includes)|測試是否一個排序的範圍包含第二個排序範圍中的所有項目。|  
|[inplace_merge (STL/CLR)](#inplace_merge)|將兩個連續排序範圍中的項目結合成單一排序範圍中。|  
|[iter_swap (STL/CLR)](#iter_swap)|交換由一組指定之迭代器所參考的兩個值。|  
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|比較兩個序列，由項目，識別序列的兩個較小者。|  
|[lower_bound (STL/CLR)](#lower_bound)|在已排序的值，其值大於或等於指定的值中尋找第一個元素的位置。|  
|[make_heap (STL/CLR)](#make_heap)|從指定的範圍將項目轉換在堆積上的第一個項目所在的最大的堆積。|  
|[最大值 (STL/CLR)](#max))|比較兩個物件，並傳回的兩個較大者。|  
|[max_element (STL/CLR)](#max_element)|尋找最大的項目中指定的順序的值。|  
|[merge (STL/CLR)](#merge))|將兩個排序的來源範圍的所有項目結合成單一排序目的範圍中。|  
|[min (STL/CLR)](#min)|比較兩個物件，並傳回兩個較小者。|  
|[min_element (STL/CLR)](#min_element)|尋找最小的項目中指定的順序的值。|  
|[mismatch (STL/CLR)](#mismatch)|比較兩個範圍的項目並傳回差異發生的第一個位置。|  
|[next_permutation (STL/CLR)](#next_permutation)|讓原始順序由語彙方面下一個較大的排列取代若有的話，請重新排列範圍中的項目。|  
|[nth_element (STL/CLR)](#nth_element)|分割序列的項目正確放入`n`個序列項目，讓它前面的所有項目都小於或等於它，並在它後面的所有元素都是大於或等於它。|  
|[partial_sort (STL/CLR)](#partial_sort)|遞減的順序排列的較小的項目範圍中指定的數目。|  
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|從來源範圍會複製項目到目的範圍，排序來源範圍中的項目。|  
|[partition (STL/CLR)](#partition)|範圍中的項目排列，以便滿足一元述詞的那些項目之前，這無法滿足。|  
|[pop_heap (STL/CLR)](#pop_heap)|從堆積的前面的最大的項目移動至結尾，然後會形成新的堆積，從其餘項目。|  
|[prev_permutation (STL/CLR)](#prev_permutation)|讓原始順序由語彙方面上一個較大的排列取代若有的話，請重新排列項目序列。|  
|[push_heap (STL/CLR)](#push_heap)|將在範圍結尾的項目加入至由範圍中之前項目所組成的現有堆積。|  
|[random_shuffle (STL/CLR)](#random_shuffle)|重新排列的一連串`N`的其中一個範圍中的項目`N`！ 排列方式隨機選取的其中一個。|  
|[remove (STL/CLR)](#remove)|從指定範圍中刪除指定的值，而不會干擾其餘項目的順序，並傳回沒有指定值的新範圍的結尾。|  
|[remove_copy (STL/CLR)](#remove_copy)|從來源範圍會複製項目到目的範圍中，不同之處在於指定的值的項目不會複製，而不會干擾其餘項目的順序。|  
|[remove_copy_if (STL/CLR)](#remove_copy_if)|複製項目從來源範圍到目的範圍，除了滿足述詞，而不會干擾其餘項目的順序。|  
|[remove_if (STL/CLR)](#remove_if)|刪除不會干擾其餘項目的順序滿足述詞，從指定範圍的項目。 .|  
|[replace (STL/CLR)](#replace)|取代範圍中符合指定的值，以新值的項目。|  
|[replace_copy (STL/CLR)](#replace_copy)|複製項目從來源範圍到目的範圍，取代項目符合指定的值，以新值。|  
|[replace_copy_if (STL/CLR)](#replace_copy_if)|檢查來源範圍內的每個項目，如果滿足指定的述詞則予以取代，同時將結果複製到新目的範圍。|  
|[replace_if (STL/CLR)](#replace_if)|檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。|  
|[reverse (STL/CLR)](#reverse)|反轉範圍內項目的順序。|  
|[reverse_copy (STL/CLR)](#reverse_copy)|反轉來源範圍內項目的順序，並將其複製到目的範圍。|  
|[rotate (STL/CLR)](#rotate)|交換兩個相鄰範圍的項目。|  
|[rotate_copy (STL/CLR)](#rotate_copy)|交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。|  
|[search (STL/CLR)](#search_)|在目標範圍中搜尋第一個序列，其項目等於指定項目序列中的項目，或在二元述詞指定的意義上，其項目相當於指定序列中的項目。|  
|[search_n (STL/CLR)](#search_n)|在範圍中搜尋包含指定項目數的第一個子序列，這些項目具有特定值或在二元述詞指定的意義上與該值關聯。|  
|[set_difference (STL/CLR)](#set_difference)|將屬於一個排序來源範圍但不屬於第二個排序來源範圍的所有項目聯集為單一排序的目的範圍，其中順序準則可由二元述詞指定。|  
|[set_intersection (STL/CLR)](#set_intersection)|將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|將屬於兩個排序來源範圍之一 (但非兩者) 的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[set_union (STL/CLR)](#set_union))|將至少屬於兩個排序來源範圍之一的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。|  
|[sort (STL/CLR)](#sort)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則。|  
|[sort_heap (STL/CLR)](#sort_heap)|將堆積轉換為排序的範圍。|  
|[stable_partition (STL/CLR)](#stable_partition)|將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前，保留對等項目的相對順序。|  
|[stable_sort (STL/CLR)](#stable_sort)|將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則，並保留對等項目的相對順序。|  
|[swap (STL/CLR)](#swap)|在兩種類型的物件之間交換項目的值，將第一個物件的內容指派給第二個物件，並將第一個物件的內容指派給第一個物件。|  
|[swap_ranges (STL/CLR)](#swap_ranges)|將某個範圍的項目與另一個相等大小之範圍的項目交換。|  
|[transform (STL/CLR)](#transform)|將指定的函式物件應用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。|  
|[unique (STL/CLR)](#unique)|移除在指定範圍內彼此相鄰的重複項目。|  
|[unique_copy (STL/CLR)](#unique_copy)|將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。|  
|[upper_bound (STL/CLR)](#upper_bound)|在已排序範圍中尋找值大於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。|  
 
## <a name="members"></a>成員

## <a name="adjacent_find"></a> adjacent_find (STL/CLR)
搜尋等於或符合指定之條件的兩個相鄰項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`adjacent_find`。 如需詳細資訊，請參閱 < [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)。

## <a name="binary_search"></a> binary_search (STL/CLR)
測試已排序的範圍中是否有等於指定之值 (或在二元述詞指定的意義上，相當於該值) 的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`binary_search`。 如需詳細資訊，請參閱 < [binary_search](../standard-library/algorithm-functions.md#binary_search)。  
  
## <a name="copy"></a> 複製 (STL/CLR)
從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以正向方向指派它們新位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`copy`。 如需詳細資訊，請參閱 <<c0> [ 複製](../standard-library/algorithm-functions.md#copy)。 

## <a name="copy_backward"></a> copy_backward (STL/CLR)
從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以反向方向指派它們新位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt1, class _BidIt2> inline  
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,  
        _BidIt2 _Dest);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`copy_backward`。 如需詳細資訊，請參閱 < [copy_backward](../standard-library/algorithm-functions.md#copy_backward)。  

## <a name="count"></a> count (STL/CLR)
傳回範圍中值符合指定值的項目數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _Ty> inline  
    typename iterator_traits<_InIt>::difference_type  
        count(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`count`。 如需詳細資訊，請參閱 <<c0> [ 計數](../standard-library/algorithm-functions.md#count)。 

## <a name="count_if"></a> count_if (STL/CLR)
傳回範圍中值符合指定條件的項目數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _Pr> inline  
    typename iterator_traits<_InIt>::difference_type  
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`count_if`。 如需詳細資訊，請參閱 < [count_if](../standard-library/algorithm-functions.md#count_if)。  
  
## <a name="equal"></a> 等於 (STL/CLR)
逐一比較兩個範圍的每個項目是否相等 (或在二元述詞指定的意義上，是否對等)。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2> inline  
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`equal`。 如需詳細資訊，請參閱 <<c0> [ 等於](../standard-library/algorithm-functions.md#equal)。  

## <a name="equal_range"></a> equal_range (STL/CLR)
在已排序的範圍中尋找一對位置，第一個位置小於或等於指定項目的位置，第二個位置大於該項目的位置，其中用於建立序列中位置的等價或順序意義可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`equal_range`。 如需詳細資訊，請參閱 < [equal_range](../standard-library/algorithm-functions.md#equal_range)。  

## <a name="fill"></a> 填滿 (STL/CLR)
將相同的新值指派到指定範圍內的每個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`fill`。 如需詳細資訊，請參閱 <<c0> [ 填滿](../standard-library/algorithm-functions.md#fill)。 

## <a name="fill_n"></a> fill_n (STL/CLR)
將新值指派給範圍中以特定元素開頭的指定元素數目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _OutIt, class _Diff, class _Ty> inline  
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`fill_n`。 如需詳細資訊，請參閱 < [fill_n](../standard-library/algorithm-functions.md#fill_n)。  

## <a name="find"></a> find (STL/CLR)
在範圍中找出有指定值的第一個項目的位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _Ty> inline  
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`find`。 如需詳細資訊，請參閱 <<c0> [ 尋找](../standard-library/algorithm-functions.md#find)。 

## <a name="find_end"></a> find_end (STL/CLR)
在範圍中尋找與指定序列相同 (或在二元述詞指定的意義上，相當於該序列) 的最後一個子序列。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`find_end`。 如需詳細資訊，請參閱 < [find_end](../standard-library/algorithm-functions.md#find_end)。  

## <a name="find_first_of"></a> find_first_of (STL/CLR)
在目標範圍內搜尋第一次出現的任何多個值，或第一次出現的任何多個項目 (在二元述詞指定的意義上，相當於指定之項目集合)。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`find_first_of`。 如需詳細資訊，請參閱 < [find_first_of](../standard-library/algorithm-functions.md#find_first_of)。  

## <a name="find_if"></a> find_if (STL/CLR)
在範圍中找出滿足特定條件的第一個項目的位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _Pr> inline  
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`find_if`。 如需詳細資訊，請參閱 < [find_if](../standard-library/algorithm-functions.md#find_if)。 

## <a name="for_each"></a> for_each (STL/CLR)
將指定的函式物件以正向順序套用至範圍內的每個項目，並傳回函式物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _Fn1> inline  
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`for_each`。 如需詳細資訊，請參閱 < [for_each](../standard-library/algorithm-functions.md#for_each)。  

## <a name="generate"></a> 產生 (STL/CLR)
將函式物件產生的值指派給範圍內的每個項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Fn0> inline  
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`generate`。 如需詳細資訊，請參閱 <<c0> [ 產生](../standard-library/algorithm-functions.md#generate)。  

## <a name="generate_n"></a> generate_n (STL/CLR)
將函式物件產生的值指派給範圍內的指定項目數，並返回到超過最後一個指定值的位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _OutIt, class _Diff, class _Fn0> inline  
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`generate_n`。 如需詳細資訊，請參閱 < [generate_n](../standard-library/algorithm-functions.md#generate_n)。  
 
## <a name="includes"></a> 包含 (STL/CLR)
測試一個排序範圍是否包含第二個排序範圍內的所有項目，其中項目之間的順序或等價準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool includes(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`includes`。 如需詳細資訊，請參閱 <<c0> [ 包含](../standard-library/algorithm-functions.md#includes)。  

## <a name="inplace_merge"></a> inplace_merge (STL/CLR)
將兩個連續排序範圍內的項目結合成單一排序範圍，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`inplace_merge`如需詳細資訊，請參閱 < [inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)。  
  
## <a name="iter_swap"></a> iter_swap (STL/CLR)
交換由一組指定之迭代器所參考的兩個值。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt1, class _FwdIt2> inline  
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`iter_swap`。 如需詳細資訊，請參閱 < [iter_swap](../standard-library/algorithm-functions.md#iter_swap)。  

## <a name="lexicographical_compare"></a> lexicographical_compare (STL/CLR)
逐一比較兩個序列之間的每個項目，判斷兩者較小者。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2> inline  
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`lexicographical_compare`。 如需詳細資訊，請參閱 < [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare)。  

## <a name="lower_bound"></a> lower_bound (STL/CLR)
尋找第一個元素的位置中的已排序的範圍，其值小於或等於指定的值，其中順序準則可指定在二元述詞。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`lower_bound`。 如需詳細資訊，請參閱 < [lower_bound](../standard-library/algorithm-functions.md#lower_bound)。  

## <a name="make_heap"></a> make_heap (STL/CLR)
將在指定範圍內的項目轉換為堆積，其中第一個項目是最大，而且排序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void make_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`make_heap`。 如需詳細資訊，請參閱 < [make_heap](../standard-library/algorithm-functions.md#make_heap)。  
  
## <a name="max"></a> 最大值 (STL/CLR)
比較兩個物件並傳回兩者較大者，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _Ty> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`max`。 如需詳細資訊，請參閱 < [max](../standard-library/algorithm-functions.md#max)。  

## <a name="max_element"></a> max_element (STL/CLR)
在指定的範圍內尋找第一個最大項目，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`max_element`。 如需詳細資訊，請參閱 < [max_element](../standard-library/algorithm-functions.md#max_element)。  

## <a name="merge"></a> merge (STL/CLR)
將兩個排序來源範圍內的所有項目結合成單一排序目的範圍，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`merge`。 如需詳細資訊，請參閱 <<c0> [ 合併](../standard-library/algorithm-functions.md#merge)。  

## <a name="min"></a> 最小值 (STL/CLR)
比較兩個物件並傳回兩者較小者，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _Ty> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`min`。 如需詳細資訊，請參閱 < [min](../standard-library/algorithm-functions.md#min)。  

## <a name="min_element"></a> min_element (STL/CLR)
在指定的範圍內尋找第一個最小項目，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`min_element`。 如需詳細資訊，請參閱 < [min_element](../standard-library/algorithm-functions.md#min_element)。  
  
## <a name="mismatch"></a> 不相符 (STL/CLR)
逐一比較兩個範圍的每個項目是否相等 (或在二元述詞指定的意義上，是否對等)，而且找出差異發生的第一個位置。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
            _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`mismatch`。 如需詳細資訊，請參閱 <<c0> [ 不符](../standard-library/algorithm-functions.md#mismatch)。  

## <a name="next_permutation"></a> next_permutation (STL/CLR)
重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 (如果有的話)，其中下一個的意義可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp 
template<class _BidIt> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`next_permutation`。 如需詳細資訊，請參閱 < [next_permutation](../standard-library/algorithm-functions.md#next_permutation)。  
  
## <a name="nth_element"></a> nth_element (STL/CLR)
分割某範圍的項目正確放入`n`個序列的項目範圍內，因此，在其前面的所有項目都小於或等於它，而且序列中在它後面的所有項目有大於或等於它。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`nth_element`。 如需詳細資訊，請參閱 < [nth_element](../standard-library/algorithm-functions.md#nth_element)。  

## <a name="partial_sort"></a> partial_sort (STL/CLR)
將範圍中指定的較小項目數目排列成非遞減排列，或是依據二元述詞指定的順序準則。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`partial_sort`。 如需詳細資訊，請參閱 < [partial_sort](../standard-library/algorithm-functions.md#partial_sort)。 

## <a name="partial_sort_copy"></a> partial_sort_copy (STL/CLR)
從來源範圍將項目複製到目的範圍，其中來源項目是依小於排序，或依據二元述詞指定的順序準則。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _RanIt> inline  
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,  
        _RanIt _First2, _RanIt _Last2);  
template<class _InIt, class _RanIt, class _Pr> inline  
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,  
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`partial_sort_copy`。 如需詳細資訊，請參閱 < [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)。  
  
## <a name="partition"></a> partition (STL/CLR)
將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt, class _Pr> inline  
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`partition`。 如需詳細資訊，請參閱 <<c0> [ 分割區](../standard-library/algorithm-functions.md#partition)。  

## <a name="pop_heap"></a> pop_heap (STL/CLR)
從堆積的前面移動最大的項目至範圍的倒數第二個位置，然後從其餘項目形成新的堆積。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void pop_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`pop_heap`。 如需詳細資訊，請參閱 < [pop_heap](../standard-library/algorithm-functions.md#pop_heap)。  

## <a name="prev_permutation"></a> prev_permutation (STL/CLR)
重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 (如果有的話)，其中下一個的意義可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`prev_permutation`。 如需詳細資訊，請參閱 < [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)。  

## <a name="push_heap"></a> push_heap (STL/CLR)
將在範圍結尾的項目加入至由範圍中之前項目所組成的現有堆積。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void push_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`push_heap`。 如需詳細資訊，請參閱 < [push_heap](../standard-library/algorithm-functions.md#push_heap)。  

## <a name="random_shuffle"></a> random_shuffle (STL/CLR)
重新排列的一連串`N`的其中一個範圍中的項目`N`！ 排列方式隨機選取的其中一個。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void random_shuffle(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Fn1> inline  
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`random_shuffle`。 如需詳細資訊，請參閱 < [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)。 

## <a name="remove"></a> 移除 (STL/CLR)
從指定範圍中排除指定的值，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`remove`。 如需詳細資訊，請參閱 <<c0> [ 移除](../standard-library/algorithm-functions.md#remove)。  

## <a name="remove_copy"></a> remove_copy (STL/CLR)
從來源範圍將項目複製到目的範圍，不過不會複製一個指定值的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt remove_copy(_InIt _First, _InIt _Last,  
        _OutIt _Dest, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`remove_copy`。 如需詳細資訊，請參閱 < [remove_copy](../standard-library/algorithm-functions.md#remove_copy)。  

## <a name="remove_copy_if"></a> remove_copy_if (STL/CLR)
從來源範圍將項目複製到目的範圍，不過不會複製滿足述詞的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`remove_copy_if`。 如需詳細資訊，請參閱 < [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)。  
  
## <a name="remove_if"></a> remove_if (STL/CLR)
從指定範圍中排除滿足述詞的項目，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Pr> inline  
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`remove_if`。 如需詳細資訊，請參閱 < [remove_if](../standard-library/algorithm-functions.md#remove_if)。  
  
## <a name="replace"></a> replace (STL/CLR)
檢查範圍內的每個項目，如果符合指定的值則予以取代。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace`。 如需詳細資訊，請參閱 <<c0> [ 取代](../standard-library/algorithm-functions.md#replace)。

## <a name="replace_copy"></a> replace_copy (STL/CLR)
檢查來源範圍內的每個項目，如果符合指定的值則予以取代，同時將結果複製到新目的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace_copy`。 如需詳細資訊，請參閱 < [replace_copy](../standard-library/algorithm-functions.md#replace_copy)。  

## <a name="replace_copy_if"></a> replace_copy_if (STL/CLR)
檢查來源範圍內的每個項目，如果滿足指定的述詞則予以取代，同時將結果複製到新目的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline  
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred, const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace_copy_if`。 如需詳細資訊，請參閱 < [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)。  
  
## <a name="replace_if"></a> replace_if (STL/CLR)
檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Pr, class _Ty> inline  
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,  
        const _Ty% _Val);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace_if`。 如需詳細資訊，請參閱 < [replace_if](../standard-library/algorithm-functions.md#replace_if)。  

## <a name="reverse"></a> reverse (STL/CLR)
反轉範圍內項目的順序。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt> inline  
    void reverse(_BidIt _First, _BidIt _Last);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`reverse`。 如需詳細資訊，請參閱 <<c0> [ 反向](../standard-library/algorithm-functions.md#reverse)。  

## <a name="reverse_copy"></a> reverse_copy (STL/CLR)
反轉來源範圍內項目的順序，並將其複製到目的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`reverse_copy`。 如需詳細資訊，請參閱 < [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)。  
  
## <a name="rotate"></a> 旋轉 (STL/CLR)
交換兩個相鄰範圍的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt> inline  
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`rotate`。 如需詳細資訊，請參閱 <<c0> [ 旋轉](../standard-library/algorithm-functions.md#rotate)。  

## <a name="rotate_copy"></a> rotate_copy (STL/CLR)
交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _OutIt> inline  
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,  
        _OutIt _Dest);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`rotate_copy`。 如需詳細資訊，請參閱 < [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)。  
  
## <a name="search_"></a> 搜尋 (STL/CLR)
在目標範圍中搜尋第一個序列，其項目等於指定項目序列中的項目，或在二元述詞指定的意義上，其項目相當於指定序列中的項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2);  
template<class _FwdIt1, class _FwdIt2, class _Pr> inline  
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`search`。 如需詳細資訊，請參閱 <<c0> [ 搜尋](../standard-library/algorithm-functions.md#search)。  

## <a name="search_n"></a> search_n (STL/CLR)
在範圍中搜尋包含指定項目數的第一個子序列，這些項目具有特定值或在二元述詞指定的意義上與該值關聯。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt1, class _Diff2, class _Ty> inline  
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _Diff2 _Count, const _Ty& _Val);  
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline  
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`search_n`。 如需詳細資訊，請參閱 < [search_n](../standard-library/algorithm-functions.md#search_n)。  

## <a name="set_difference"></a> set_difference (STL/CLR)
將屬於一個排序來源範圍但不屬於第二個排序來源範圍的所有項目聯集為單一排序的目的範圍，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`set_difference`。 如需詳細資訊，請參閱 < [set_difference](../standard-library/algorithm-functions.md#set_difference)。

## <a name="set_intersection"></a> set_intersection (STL/CLR)
將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`set_intersection`。 如需詳細資訊，請參閱 < [set_intersection](../standard-library/algorithm-functions.md#set_intersection)。 

## <a name="set_symmetric_difference"></a> set_symmetric_difference (STL/CLR)
將屬於兩個排序來源範圍之一 (但非兩者) 的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`set_symmetric_difference`。 如需詳細資訊，請參閱 < [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)。  

## <a name="set_union"></a> set_union (STL/CLR)
將至少屬於兩個排序來源範圍之一的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`set_union`。 如需詳細資訊，請參閱 < [set_union](../standard-library/algorithm-functions.md#set_union)。  

## <a name="sort"></a> 排序 (STL/CLR)
將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void sort(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`sort`。 如需詳細資訊，請參閱 <<c0> [ 排序](../mfc/reference/cmfclistctrl-class.md#sort)。  

## <a name="sort_heap"></a> sort_heap (STL/CLR)
將堆積轉換為排序的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _RanIt> inline  
    void sort_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`sort_heap`。 如需詳細資訊，請參閱 < [sort_heap](../standard-library/algorithm-functions.md#sort_heap)。  

## <a name="stable_partition"></a> stable_partition (STL/CLR)
將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前，保留對等項目的相對順序。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt, class _Pr> inline  
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`stable_partition`。 如需詳細資訊，請參閱 < [stable_partition](../standard-library/algorithm-functions.md#stable_partition)。  

## <a name="stable_sort"></a> stable_sort (STL/CLR)
將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則，並保留對等項目的相對順序。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _BidIt> inline  
    void stable_sort(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`stable_sort`。 如需詳細資訊，請參閱 < [stable_sort](../standard-library/algorithm-functions.md#stable_sort)。  
  
## <a name="swap"></a> swap (STL/CLR)
在兩種類型的物件之間交換項目的值，將第一個物件的內容指派給第二個物件，並將第一個物件的內容指派給第一個物件。  
  
### <a name="syntax"></a>語法  
  
```cpp  
<class _Ty> inline  
    void swap(_Ty% _Left, _Ty% _Right);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`swap`。 如需詳細資訊，請參閱 <<c0> [ 交換](../standard-library/algorithm-functions.md#swap)。  

## <a name="swap_ranges"></a> swap_ranges (STL/CLR)
將某個範圍的項目與另一個相等大小之範圍的項目交換。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`swap_ranges`。 如需詳細資訊，請參閱 < [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)。  

## <a name="transform"></a> 轉換 (STL/CLR)
將指定的函式物件應用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt, class _Fn1> inline  
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Fn1 _Func);  
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline  
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`transform`。 如需詳細資訊，請參閱 <<c0> [ 轉換](../standard-library/algorithm-functions.md#transform)。  

## <a name="unique"></a> 唯一 (STL/CLR)
移除在指定範圍內彼此相鄰的重複項目。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`unique`。 如需詳細資訊，請參閱 <<c0> [ 唯一](../standard-library/algorithm-functions.md#unique)。  
  
## <a name="unique_copy"></a> unique_copy (STL/CLR)
將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _InIt, class _OutIt> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`unique_copy`。 如需詳細資訊，請參閱 < [unique_copy](../standard-library/algorithm-functions.md#unique_copy)。  

## <a name="upper_bound"></a> upper_bound (STL/CLR)
在已排序範圍中尋找值大於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。  
  
### <a name="syntax"></a>語法  
  
```cpp  
template<class _FwdIt, class _Ty> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
### <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`upper_bound`。 如需詳細資訊，請參閱 < [upper_bound](../standard-library/algorithm-functions.md#upper_bound)。 