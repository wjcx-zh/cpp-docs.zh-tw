---
title: "unordered_multimap 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_multimap
- std::unordered_multimap
- unordered_map/std::unordered_multimap
- std::unordered_multimap::allocator_type
- unordered_map/std::unordered_multimap::allocator_type
- std::unordered_multimap::const_iterator
- unordered_map/std::unordered_multimap::const_iterator
- std::unordered_multimap::const_local_iterator
- unordered_map/std::unordered_multimap::const_local_iterator
- std::unordered_multimap::const_pointer
- unordered_map/std::unordered_multimap::const_pointer
- std::unordered_multimap::const_reference
- unordered_map/std::unordered_multimap::const_reference
- std::unordered_multimap::difference_type
- unordered_map/std::unordered_multimap::difference_type
- std::unordered_multimap::hasher
- unordered_map/std::unordered_multimap::hasher
- std::unordered_multimap::iterator
- unordered_map/std::unordered_multimap::iterator
- std::unordered_multimap::key_equal
- unordered_map/std::unordered_multimap::key_equal
- std::unordered_multimap::key_type
- unordered_map/std::unordered_multimap::key_type
- std::unordered_multimap::local_iterator
- unordered_map/std::unordered_multimap::local_iterator
- std::unordered_multimap::mapped_type
- unordered_map/std::unordered_multimap::mapped_type
- std::unordered_multimap::pointer
- unordered_map/std::unordered_multimap::pointer
- std::unordered_multimap::reference
- unordered_map/std::unordered_multimap::reference
- std::unordered_multimap::size_type
- unordered_map/std::unordered_multimap::size_type
- std::unordered_multimap::value_type
- unordered_map/std::unordered_multimap::value_type
- std::unordered_multimap::begin
- unordered_map/std::unordered_multimap::begin
- std::unordered_multimap::bucket
- unordered_map/std::unordered_multimap::bucket
- std::unordered_multimap::bucket_count
- unordered_map/std::unordered_multimap::bucket_count
- std::unordered_multimap::bucket_size
- unordered_map/std::unordered_multimap::bucket_size
- std::unordered_multimap::cbegin
- unordered_map/std::unordered_multimap::cbegin
- std::unordered_multimap::cend
- unordered_map/std::unordered_multimap::cend
- std::unordered_multimap::clear
- unordered_map/std::unordered_multimap::clear
- std::unordered_multimap::count
- unordered_map/std::unordered_multimap::count
- std::unordered_multimap::emplace
- unordered_map/std::unordered_multimap::emplace
- std::unordered_multimap::emplace_hint
- unordered_map/std::unordered_multimap::emplace_hint
- std::unordered_multimap::empty
- unordered_map/std::unordered_multimap::empty
- std::unordered_multimap::end
- unordered_map/std::unordered_multimap::end
- std::unordered_multimap::equal_range
- unordered_map/std::unordered_multimap::equal_range
- std::unordered_multimap::erase
- unordered_map/std::unordered_multimap::erase
- std::unordered_multimap::find
- unordered_map/std::unordered_multimap::find
- std::unordered_multimap::get_allocator
- unordered_map/std::unordered_multimap::get_allocator
- std::unordered_multimap::hash_function
- unordered_map/std::unordered_multimap::hash_function
- std::unordered_multimap::insert
- unordered_map/std::unordered_multimap::insert
- std::unordered_multimap::key_eq
- unordered_map/std::unordered_multimap::key_eq
- std::unordered_multimap::load_factor
- unordered_map/std::unordered_multimap::load_factor
- std::unordered_multimap::max_bucket_count
- unordered_map/std::unordered_multimap::max_bucket_count
- std::unordered_multimap::max_load_factor
- unordered_map/std::unordered_multimap::max_load_factor
- std::unordered_multimap::max_size
- unordered_map/std::unordered_multimap::max_size
- std::unordered_multimap::rehash
- unordered_map/std::unordered_multimap::rehash
- std::unordered_multimap::size
- unordered_map/std::unordered_multimap::size
- std::unordered_multimap::swap
- unordered_map/std::unordered_multimap::swap
- std::unordered_multimap::unordered_multimap
- unordered_map/std::unordered_multimap::unordered_multimap
- std::unordered_multimap::operator=
- unordered_map/std::unordered_multimap::operator=
dev_langs:
- C++
helpviewer_keywords:
- unordered_multimap class
ms.assetid: 4baead6c-5870-4b85-940f-a47d6b891c27
caps.latest.revision: 28
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8c27a26f0e65066405694652be9d46937642043f
ms.lasthandoff: 02/24/2017

---
# <a name="unorderedmultimap-class"></a>unordered_multimap 類別
此樣板類別描述控制不同長度的 `std::pair<const Key, Ty>` 類型項目序列的物件。 序列由雜湊函式弱式排序，將序列分割為子序列的已排序集合，稱為 Bucket。 在每個 Bucket 中，比較函式判斷是否有任何一對項目具有對等順序。 每個項目儲存兩個物件：排序鍵和值。 序列表示允許以一些作業查閱、插入和移除任意項目，這些作業可以獨立於序列中的項目數目 (常數時間)，至少當所有 Bucket 長度大約相等時。 在最壞的情況下，當所有項目都在一個 Bucket 時，作業數目與序列中的項目數目成正比 (線性時間)。 此外，插入項目不會使任何迭代器無效，移除項目則僅會使指向被移除項目的迭代器無效。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Key,  
    class Ty,  
    class Hash = std::hash<Key>,  
    class Pred = std::equal_to<Key>,  
    class Alloc = std::allocator<Key>>  
class unordered_multimap;  
```  
  
#### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`Key`|索引鍵類型。|  
|`Ty`|對應的類型。|  
|`Hash`|雜湊函式物件類型。|  
|`Pred`|相等比較函式物件類型。|  
|`Alloc`|配置器類別。|  
  
## <a name="members"></a>Members  
  
|||  
|-|-|  
|類型定義|說明|  
|[unordered_multimap::allocator_type](#unordered_multimap__allocator_type)|管理儲存體的配置器類型。|  
|[unordered_multimap::const_iterator](#unordered_multimap__const_iterator)|用於受控制序列的常數迭代器類型。|  
|[unordered_multimap::const_local_iterator](#unordered_multimap__const_local_iterator)|用於受控制序列的常數 Bucket 迭代器類型。|  
|[unordered_multimap::const_pointer](#unordered_multimap__const_pointer)|項目的常數指標類型。|  
|[unordered_multimap::const_reference](#unordered_multimap__const_reference)|項目的常數參考類型。|  
|[unordered_multimap::difference_type](#unordered_multimap__difference_type)|兩個項目之間帶正負號距離的類型。|  
|[unordered_multimap::hasher](#unordered_multimap__hasher)|雜湊函式的類型。|  
|[unordered_multimap::iterator](#unordered_multimap__iterator)|受控制序列之迭代器的類型。|  
|[unordered_multimap::key_equal](#unordered_multimap__key_equal)|比較函式的類型。|  
|[unordered_multimap::key_type](#unordered_multimap__key_type)|排序索引鍵的類型。|  
|[unordered_multimap::local_iterator](#unordered_multimap__local_iterator)|用於受控制序列的 Bucket 迭代器類型。|  
|[unordered_multimap::mapped_type](#unordered_multimap__mapped_type)|與每個索引鍵關聯的對應值類型。|  
|[unordered_multimap::pointer](#unordered_multimap__pointer)|項目的指標類型。|  
|[unordered_multimap::reference](#unordered_multimap__reference)|項目的參考類型。|  
|[unordered_multimap::size_type](#unordered_multimap__size_type)|兩個項目之間不帶正負號距離的類型。|  
|[unordered_multimap::value_type](#unordered_multimap__value_type)|元素的類型。|  
  
|||  
|-|-|  
|成員函式|說明|  
|[unordered_multimap::begin](#unordered_multimap__begin)|指定受控制序列的開頭。|  
|[unordered_multimap::bucket](#unordered_multimap__bucket)|取得索引鍵值的值區數目。|  
|[unordered_multimap::bucket_count](#unordered_multimap__bucket_count)|取得 Bucket 的數目。|  
|[unordered_multimap::bucket_size](#unordered_multimap__bucket_size)|取得 Bucket 大小。|  
|[unordered_multimap::cbegin](#unordered_multimap__cbegin)|指定受控制序列的開頭。|  
|[unordered_multimap::cend](#unordered_multimap__cend)|指定受控制序列的結尾。|  
|[unordered_multimap::clear](#unordered_multimap__clear)|移除所有項目。|  
|[unordered_multimap::count](#unordered_multimap__count)|尋找符合指定索引鍵的項目數目。|  
|[unordered_multimap::emplace](#unordered_multimap__emplace)|加入就地建構的項目。|  
|[unordered_multimap::emplace_hint](#unordered_multimap__emplace_hint)|加入就地建構的項目，含提示。|  
|[unordered_multimap::empty](#unordered_multimap__empty)|測試項目是否不存在。|  
|[unordered_multimap::end](#unordered_multimap__end)|指定受控制序列的結尾。|  
|[unordered_multimap::equal_range](#unordered_multimap__equal_range)|尋找符合指定之索引鍵的範圍。|  
|[unordered_multimap::erase](#unordered_multimap__erase)|移除位於指定位置的項目。|  
|[unordered_multimap::find](#unordered_multimap__find)|尋找符合指定之索引鍵的元素。|  
|[unordered_multimap::get_allocator](#unordered_multimap__get_allocator)|取得已儲存的配置器物件。|  
|[unordered_multimap::hash_function](#unordered_multimap__hash_function)|取得儲存的雜湊函式物件。|  
|[unordered_multimap::insert](#unordered_multimap__insert)|加入項目。|  
|[unordered_multimap::key_eq](#unordered_multimap__key_eq)|取得儲存的比較函式物件。|  
|[unordered_multimap::load_factor](#unordered_multimap__load_factor)|計算每個值區的平均項目數。|  
|[unordered_multimap::max_bucket_count](#unordered_multimap__max_bucket_count)|取得 Bucket 最大數目。|  
|[unordered_multimap::max_load_factor](#unordered_multimap__max_load_factor)|取得或設定每個 Bucket 最大項目數。|  
|[unordered_multimap::max_size](#unordered_multimap__max_size)|取得受控制序列的大小上限。|  
|[unordered_multimap::rehash](#unordered_multimap__rehash)|重建雜湊資料表。|  
|[unordered_multimap::size](#unordered_multimap__size)|計算元素的數目。|  
|[unordered_multimap::swap](#unordered_multimap__swap)|交換兩個容器的內容。|  
|[unordered_multimap::unordered_multimap](#unordered_multimap__unordered_multimap)|建構容器物件。|  
  
|||  
|-|-|  
|運算子|說明|  
|[unordered_multimap::operator=](#unordered_multimap__operator_eq)|複製雜湊資料表。|  
  
## <a name="remarks"></a>備註  
 物件會排列它所控制之序列的順序，方式是呼叫兩個預存物件，一個是 [unordered_multimap::key_equal](#unordered_multimap__key_equal) 類型的比較函式物件，一個是 [unordered_multimap::hasher](#unordered_multimap__hasher) 類型的雜湊函式物件。 您可以透過呼叫成員函式 [unordered_multimap::key_eq](#unordered_multimap__key_eq)`()` 存取第一個預存物件；透過呼叫成員函式 [unordered_multimap::hash_function](#unordered_multimap__hash_function)`()` 存取第二個預存物件。 具體來說，只有在兩個引數值具有對等順序，對於 `X` 類型的所有值 `Y` 和 `Key`，呼叫 `key_eq()(X, Y)` 才會傳回 true，呼叫 `hash_function()(keyval)` 會產生 `size_t` 類型值的分佈。 不同於樣板類別 [unordered_map 類別](../standard-library/unordered-map-class.md)，樣板類別 `unordered_multimap` 的物件並不保證 `key_eq()(X, Y)` 針對受控制序列的任何兩個元素永遠是 false。 (索引鍵不需要是唯一的)。  
  
 物件也會儲存最大載入因數，指定每個 Bucket 所需的項目平均數目上限。 如果插入元素會使 [unordered_multimap::load_factor](#unordered_multimap__load_factor)`()` 超出最大的載入因數，容器會增加值區的數目並視需要重建雜湊資料表。  
  
 受控制序列中實際的項目順序取決於雜湊函式、比較函式、插入順序、最大載入因數和 Bucket 目前數目。 一般來說，您無法預測受控制序列中的項目順序。 不過，您永遠可以確保，有對等順序的任何項目子集在受控制序列中為相鄰。  
  
 物件會透過 [unordered_multimap::allocator_type](#unordered_multimap__allocator_type) 類型的預存配置器物件，配置並釋放它所控制之序列的儲存體。 這種配置器物件必須具有和 `allocator` 樣板類別物件相同的外部介面。 請注意，如果已指定容器物件，儲存的配置器物件不會複製。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<unordered_map>  
  
 **命名空間：** std  
  
##  <a name="a-nameunorderedmultimapallocatortypea--unorderedmultimapallocatortype"></a><a name="unordered_multimap__allocator_type"></a>  unordered_multimap::allocator_type  
 管理儲存體的配置器類型。  
  
```  
typedef Alloc allocator_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Alloc`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_allocator_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="a-nameunorderedmultimapbegina--unorderedmultimapbegin"></a><a name="unordered_multimap__begin"></a>  unordered_multimap::begin  
 指定受控制序列或值區的開頭。  
  
```  
iterator begin();

const_iterator begin() const;

 
local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`nbucket`|Bucket 編號。|  
  
### <a name="remarks"></a>備註  
 最前面兩個成員函式傳回的正向迭代器，指向序列的第一個項目 (或在空序列結尾以外的位置)。 最後面兩個成員函式傳回的正向迭代器，指向值區 `nbucket` 的第一個項目 (或在空值區結尾以外的位置)。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_begin.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect first two items " [c 3] [b 2]"   
    Mymap::iterator it2 = c1.begin();   
    std::cout << " [" << it2->first << ", " << it2->second << "]";   
    ++it2;   
    std::cout << " [" << it2->first << ", " << it2->second << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << lit->first << ", " << lit->second << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[c, 3] [b, 2]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapbucketa--unorderedmultimapbucket"></a><a name="unordered_multimap__bucket"></a>  unordered_multimap::bucket  
 取得索引鍵值的值區數目。  
  
```  
size_type bucket(const Key& keyval) const;
```  
  
### <a name="parameters"></a>參數  
 `keyval`  
 要對應的索引鍵值。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回目前對應至索引鍵值 `keyval`的值區數目。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_bucket.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Mymap::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="a-nameunorderedmultimapbucketcounta--unorderedmultimapbucketcount"></a><a name="unordered_multimap__bucket_count"></a>  unordered_multimap::bucket_count  
 取得 Bucket 的數目。  
  
```  
size_type bucket_count() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回目前的 Bucket 數目。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="a-nameunorderedmultimapbucketsizea--unorderedmultimapbucketsize"></a><a name="unordered_multimap__bucket_size"></a>  unordered_multimap::bucket_size  
 取得 Bucket 大小  
  
```  
size_type bucket_size(size_type nbucket) const;
```  
  
### <a name="parameters"></a>參數  
 `nbucket`  
 Bucket 編號。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回 Bucket 編號 `nbucket`的大小。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_bucket_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// display buckets for keys   
    Mymap::size_type bs = c1.bucket('a');   
    std::cout << "bucket('a') == " << bs << std::endl;   
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket('a') == 7  
bucket_size(7) == 1  
```  
  
##  <a name="a-nameunorderedmultimapcbegina--unorderedmultimapcbegin"></a><a name="unordered_multimap__cbegin"></a>  unordered_multimap::cbegin  
 傳回 `const` 迭代器，為範圍中的第一個項目定址。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 `const` 正向存取迭代器，指向範圍的第一個項目，或指向空白範圍結尾 (空白範圍 `cbegin() == cend()`) 之外的位置。  
  
### <a name="remarks"></a>備註  
 傳回值為 `cbegin` 時，無法修改範圍中的項目。  
  
 您可以使用此成員函式取代 `begin()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請考慮將 `Container` 視為支援 `begin()` 和 `cbegin()` 的各種可修改 (非 `const`) 容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-nameunorderedmultimapcenda--unorderedmultimapcend"></a><a name="unordered_multimap__cend"></a>  unordered_multimap::cend  
 傳回 `const` 迭代器，為範圍中最後一個項目之外的位置定址。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 指向範圍結尾之外的 `const` 正向存取迭代器。  
  
### <a name="remarks"></a>備註  
 `cend` 用來測試迭代器是否已超過其範圍結尾。  
  
 您可以使用此成員函式取代 `end()` 成員函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將 `Container` 視為支援 `end()` 和 `cend()` 且可修改的任何種類 (非 `const`) 容器。  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 `cend` 所傳回的值不應該取值。  
  
##  <a name="a-nameunorderedmultimapcleara--unorderedmultimapclear"></a><a name="unordered_multimap__clear"></a>  unordered_multimap::clear  
 移除所有項目。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>備註  
 成員函式呼叫 [unordered_multimap::erase](#unordered_multimap__erase)`(` [unordered_multimap::begin](#unordered_multimap__begin)`(),` [unordered_multimap::end](#unordered_multimap__end)`())`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_clear.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert(Mymap::value_type('d', 4));   
    c1.insert(Mymap::value_type('e', 5));   
  
// display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="a-nameunorderedmultimapconstiteratora--unorderedmultimapconstiterator"></a><a name="unordered_multimap__const_iterator"></a>  unordered_multimap::const_iterator  
 用於受控制序列的常數迭代器類型。  
  
```  
typedef T1 const_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型說明可做為受控制序列之常數正向迭代器的物件。 在此將其說明為實作定義類型 `T1`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_const_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapconstlocaliteratora--unorderedmultimapconstlocaliterator"></a><a name="unordered_multimap__const_local_iterator"></a>  unordered_multimap::const_local_iterator  
 用於受控制序列的常數 Bucket 迭代器類型。  
  
```  
typedef T5 const_local_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型說明可作為值區之常數正向迭代器的物件。 在此將其說明為實作定義類型 `T5`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_const_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << lit->first << ", " << lit->second << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapconstpointera--unorderedmultimapconstpointer"></a><a name="unordered_multimap__const_pointer"></a>  unordered_multimap::const_pointer  
 項目的常數指標類型。  
  
```  
typedef Alloc::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>備註  
 此類型所說明的物件可做為受控制序列之項目的常數指標。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_const_pointer.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::const_pointer p = &*it;   
        std::cout << " [" << p->first << ", " << p->second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapconstreferencea--unorderedmultimapconstreference"></a><a name="unordered_multimap__const_reference"></a>  unordered_multimap::const_reference  
 項目的常數參考類型。  
  
```  
typedef Alloc::const_reference const_reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型所說明的物件可作為受控制序列之元素的常數參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_const_reference.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::const_reference ref = *it;   
        std::cout << " [" << ref.first << ", " << ref.second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapcounta--unorderedmultimapcount"></a><a name="unordered_multimap__count"></a>  unordered_multimap::count  
 尋找符合指定索引鍵的項目數目。  
  
```  
size_type count(const Key& keyval) const;
```  
  
### <a name="parameters"></a>參數  
 `keyval`  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 成員函式傳回由 [unordered_multimap::equal_range](#unordered_multimap__equal_range)`(keyval)` 分隔之範圍中的元素數。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    std::cout << "count('A') == " << c1.count('A') << std::endl;   
    std::cout << "count('b') == " << c1.count('b') << std::endl;   
    std::cout << "count('C') == " << c1.count('C') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
count('A') == 0  
count('b') == 1  
count('C') == 0  
```  
  
##  <a name="a-nameunorderedmultimapdifferencetypea--unorderedmultimapdifferencetype"></a><a name="unordered_multimap__difference_type"></a>  unordered_multimap::difference_type  
 兩個項目之間帶正負號距離的類型。  
  
```  
typedef T3 difference_type;  
```  
  
### <a name="remarks"></a>備註  
 此帶正負號的整數類型所描述的物件可代表受控制序列中任何兩個項目位址之間的差距。 在此將其描述為已定義實作之 `T3`類型的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_difference_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// compute positive difference   
    Mymap::difference_type diff = 0;   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    std::cout << "end()-begin() == " << diff << std::endl;   
  
// compute negative difference   
    diff = 0;   
    for (Mymap::const_iterator it = c1.end();   
        it != c1.begin(); --it)   
        --diff;   
    std::cout << "begin()-end() == " << diff << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
end()-begin() == 3  
begin()-end() == -3  
```  
  
##  <a name="a-nameunorderedmultimapemplacea--unorderedmultimapemplace"></a><a name="unordered_multimap__emplace"></a>  unordered_multimap::emplace  
 插入就地建構元素 (沒有執行複製或移動作業)，其中含位置提示。  
  
```  
template <class... Args>  
iterator emplace(Args&&... args);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`args`|轉送以建構插入 unordered_multimap 之元素的引數。|  
  
### <a name="return-value"></a>傳回值  
 指向新插入之元素的迭代器。  
  
### <a name="remarks"></a>備註  
 此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。  
  
 元素的 [value_type](../standard-library/map-class.md#map__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 在插入期間，如果擲回例外狀況，但不是發生在容器的雜湊函式中，則不會修改容器。 若雜湊函式中擲回例外狀況，則結果為未定義。  
  
 如需程式碼範例，請參閱 [multimap::emplace](../standard-library/multimap-class.md#multimap__emplace)。  
  
##  <a name="a-nameunorderedmultimapemplacehinta--unorderedmultimapemplacehint"></a><a name="unordered_multimap__emplace_hint"></a>  unordered_multimap::emplace_hint  
 插入就地建構元素 (沒有執行複製或移動作業)，其中含位置提示。  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|`args`|轉送以建構插入 unordered 之元素的引數。|  
|`where`|有關要從何處開始搜尋正確插入點的提示。|  
  
### <a name="return-value"></a>傳回值  
 指向新插入之元素的迭代器。  
  
### <a name="remarks"></a>備註  
 此函式不會使容器元素的參考無效，但是可能會使容器的所有迭代器無效。  
  
 在插入期間，如果擲回例外狀況，但不是發生在容器的雜湊函式中，則不會修改容器。 若雜湊函式中擲回例外狀況，則結果為未定義。  
  
 元素的 [value_type](../standard-library/map-class.md#map__value_type) 是一個配對，因此元素的值將會是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 如需程式碼範例，請參閱 [map::emplace_hint](../standard-library/map-class.md#map__emplace_hint)。  
  
##  <a name="a-nameunorderedmultimapemptya--unorderedmultimapempty"></a><a name="unordered_multimap__empty"></a>  unordered_multimap::empty  
 測試項目是否不存在。  
  
```  
bool empty() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會對空的受控制序列傳回 true。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_empty.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert(Mymap::value_type('d', 4));   
    c1.insert(Mymap::value_type('e', 5));   
  
// display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="a-nameunorderedmultimapenda--unorderedmultimapend"></a><a name="unordered_multimap__end"></a>  unordered_multimap::end  
 指定受控制序列的結尾。  
  
```  
iterator end();

const_iterator end() const;

 
local_iterator end(size_type nbucket);

const_local_iterator end(size_type nbucket) const;
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`nbucket`|Bucket 編號。|  
  
### <a name="remarks"></a>備註  
 前兩個成員函式會傳回指向序列結尾之外的正向迭代器。 最後兩個成員函式會傳回指向 Bucket `nbucket` 結尾之外的正向迭代器。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_end.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect last two items " [a 1] [b 2]"   
    Mymap::iterator it2 = c1.end();   
    --it2;   
    std::cout << " [" << it2->first << ", " << it2->second << "]";   
    --it2;   
    std::cout << " [" << it2->first << ", " << it2->second << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Mymap::const_local_iterator lit = c1.end(c1.bucket('a'));   
    --lit;   
    std::cout << " [" << lit->first << ", " << lit->second << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1] [b, 2]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapequalrangea--unorderedmultimapequalrange"></a><a name="unordered_multimap__equal_range"></a>  unordered_multimap::equal_range  
 尋找符合指定之索引鍵的範圍。  
  
```  
std::pair<iterator, iterator>  
    equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>  
    equal_range(const Key& keyval) const;
```  
  
### <a name="parameters"></a>參數  
 `keyval`  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回一組迭代器 `X` ，使 `[X.first, X.second)` 僅分隔與 `keyval`具有相同順序之受控制序列的項目。 如果沒有這類項目存在，則兩個迭代器皆為 `end()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_equal_range.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// display results of failed search   
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =   
        c1.equal_range('x');   
    std::cout << "equal_range('x'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << pair1.first->first   
            << ", " << pair1.first->second << "]";   
    std::cout << std::endl;   
  
// display results of successful search   
    pair1 = c1.equal_range('b');   
    std::cout << "equal_range('b'):";   
    for (; pair1.first != pair1.second; ++pair1.first)   
        std::cout << " [" << pair1.first->first   
            << ", " << pair1.first->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
equal_range('x'):  
equal_range('b'): [b, 2]  
```  
  
##  <a name="a-nameunorderedmultimaperasea--unorderedmultimaperase"></a><a name="unordered_multimap__erase"></a>  unordered_multimap::erase  
 從指定的位置移除 unordered_multimap 中的元素或元素範圍，或移除符合指定索引鍵的元素。  
  
```  
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,  
    const_iterator Last);

size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>參數  
 `Where`  
 要移除之項目的位置。  
  
 `First`  
 要移除之第一個項目的位置。  
  
 `Last`  
 緊接在要移除之最後一個項目後面的位置。  
  
 `Key`  
 要移除之項目的索引鍵值。  
  
### <a name="return-value"></a>傳回值  
 在前兩個成員函式中，會傳回雙向迭代器，其中指定任何移除的元素之外剩餘的第一個元素，或者如果沒有此類元素，則傳回 map 結尾的元素。  
  
 在第三個成員函式中，傳回已從 unordered_multimap 移除的元素數。  
  
### <a name="remarks"></a>備註  
 如需程式碼範例，請參閱 [map::erase](../standard-library/map-class.md#map__erase)。  
  
##  <a name="a-nameunorderedmultimapfinda--unorderedmultimapfind"></a><a name="unordered_multimap__find"></a>  unordered_multimap::find  
 尋找符合指定之索引鍵的元素。  
  
```  
const_iterator find(const Key& keyval) const;
```  
  
### <a name="parameters"></a>參數  
 `keyval`  
 要搜尋的索引鍵值。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [unordered_multimap::equal_range](#unordered_multimap__equal_range)`(keyval).first`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_find.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// try to find and fail   
    std::cout << "find('A') == "   
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;   
  
// try to find and succeed   
    Mymap::iterator it = c1.find('b');   
    std::cout << "find('b') == "   
        << std::boolalpha << (it != c1.end())   
        << ": [" << it->first << ", " << it->second << "]" << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
find('A') == false  
find('b') == true: [b, 2]  
```  
  
##  <a name="a-nameunorderedmultimapgetallocatora--unorderedmultimapgetallocator"></a><a name="unordered_multimap__get_allocator"></a>  unordered_multimap::get_allocator  
 取得已儲存的配置器物件。  
  
```  
Alloc get_allocator() const;
```  
  
### <a name="remarks"></a>備註  
 這個成員函式會傳回儲存的配置器物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_get_allocator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
typedef std::allocator<std::pair<const char, int> > Myalloc;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::allocator_type al = c1.get_allocator();   
    std::cout << "al == std::allocator() is "   
        << std::boolalpha << (al == Myalloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
al == std::allocator() is true  
```  
  
##  <a name="a-nameunorderedmultimaphashfunctiona--unorderedmultimaphashfunction"></a><a name="unordered_multimap__hash_function"></a>  unordered_multimap::hash_function  
 取得儲存的雜湊函式物件。  
  
```  
Hash hash_function() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回儲存的雜湊函式物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_hash_function.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="a-nameunorderedmultimaphashera--unorderedmultimaphasher"></a><a name="unordered_multimap__hasher"></a>  unordered_multimap::hasher  
 雜湊函式的類型。  
  
```  
typedef Hash hasher;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Hash`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_hasher.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::hasher hfn = c1.hash_function();   
    std::cout << "hfn('a') == " << hfn('a') << std::endl;   
    std::cout << "hfn('b') == " << hfn('b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
hfn('a') == 1630279  
hfn('b') == 1647086  
```  
  
##  <a name="a-nameunorderedmultimapinserta--unorderedmultimapinsert"></a><a name="unordered_multimap__insert"></a>  unordered_multimap::insert  
 將某個元素或元素範圍插入 unordered_multimap 中。  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`Val`|要插入至 unordered_multimap 的元素值。|  
|`Where`|要開始搜尋正確的插入點的地方|  
|`ValTy`|範本參數，指定 unordered_multimap 可用於建構 [value_type](../standard-library/map-class.md#map__value_type) 之元素的引數類型，並將 `Val` 做為引數完美轉送。|  
|`First`|要複製之第一個元素的位置。|  
|`Last`|要複製之最一個元素後方的位置。|  
|`InputIterator`|符合[輸入迭代器](../standard-library/input-iterator-tag-struct.md)需求的樣板函式引數，該迭代器所指的項目屬於可用來建構 [value_type](../standard-library/map-class.md#map__value_type) 物件的類型。|  
|`IList`|要從中複製項目的 [initializer_list](../standard-library/initializer-list.md)。|  
  
### <a name="return-value"></a>傳回值  
 單一元素插入成員函式 (1) 和 (2)，會將迭代器傳回至在 unordered_multimap 中插入新元素的位置。  
  
 具有提示的單一元素成員函式 (3) 和 (4)，會傳回迭代器，其指向在 unordered_multimap 中插入新元素的位置。  
  
### <a name="remarks"></a>備註  
 此函式不會使指標或參考無效，但是可能會使容器的所有迭代器無效。  
  
 在只插入一個元素的期間，若擲出例外狀況，但沒有發生在容器的雜湊函式中，則不會修改容器的狀態。 若雜湊函式中擲回例外狀況，則結果為未定義。 在插入多個元素期間，若擲出例外狀況，則容器會處於未指定但有效的狀態。  
  
 容器的 [value_type](../standard-library/map-class.md#map__value_type) 是屬於容器的 typedef，而就 map 而言，`map<K, V>::value_type` 是 `pair<const K, V>`。 元素的值是已排序的配對，其中第一個元件等於索引鍵值，而第二個元件等於元素的資料值。  
  
 範圍成員函式 (5) 會將元素值序列插入 unordered_multimap，而 unordered_multimap 對應至範圍 `[First, Last)` 中迭代器指定的每個元素；因此不會插入 `Last`。 容器成員函式 `end()` 是指容器中最後一個元素後方的位置；例如，陳述式 `m.insert(v.begin(), v.end());` 會將 `v` 的所有元素插入至 `m`。  
  
 初始設定式清單成員函式 (6) 使用 [initializer_list](../standard-library/initializer-list.md) 將元素複製到 unordered_multimap。  
  
 針對插入就地建構的元素 (也就是沒有執行複製或移動作業)，請參閱 [unordered_multimap::emplace](#unordered_multimap__emplace) 和 [unordered_multimap::emplace_hint](#unordered_multimap__emplace_hint)。  
  
 如需程式碼範例，請參閱 [multimap::insert](../standard-library/multiset-class.md#multiset__insert)。  
  
##  <a name="a-nameunorderedmultimapiteratora--unorderedmultimapiterator"></a><a name="unordered_multimap__iterator"></a>  unordered_multimap::iterator  
 受控制序列之迭代器的類型。  
  
```  
typedef T0 iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型說明可作為受控制序列之正向迭代器的物件。 在此將其說明為實作定義類型 `T0`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapkeyeqa--unorderedmultimapkeyeq"></a><a name="unordered_multimap__key_eq"></a>  unordered_multimap::key_eq  
 取得儲存的比較函式物件。  
  
```  
Pred key_eq() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回儲存的比較函式物件  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_key_eq.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="a-nameunorderedmultimapkeyequala--unorderedmultimapkeyequal"></a><a name="unordered_multimap__key_equal"></a>  unordered_multimap::key_equal  
 比較函式的類型。  
  
```  
typedef Pred key_equal;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Pred`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_key_equal.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    Mymap::key_equal cmpfn = c1.key_eq();   
    std::cout << "cmpfn('a', 'a') == "   
        << std::boolalpha << cmpfn('a', 'a') << std::endl;   
    std::cout << "cmpfn('a', 'b') == "   
        << std::boolalpha << cmpfn('a', 'b') << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
cmpfn('a', 'a') == true  
cmpfn('a', 'b') == false  
```  
  
##  <a name="a-nameunorderedmultimapkeytypea--unorderedmultimapkeytype"></a><a name="unordered_multimap__key_type"></a>  unordered_multimap::key_type  
 排序索引鍵的類型。  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Key`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_key_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimaploadfactora--unorderedmultimaploadfactor"></a><a name="unordered_multimap__load_factor"></a>  unordered_multimap::load_factor  
 計算每個值區的平均項目數。  
  
```  
float load_factor() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式傳回 `(float)`[unordered_multimap::size](#unordered_multimap__size)`() / (float)`[unordered_multimap::bucket_count](#unordered_multimap__bucket_count)`()`，亦即每個值區的平均元素數。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
##  <a name="a-nameunorderedmultimaplocaliteratora--unorderedmultimaplocaliterator"></a><a name="unordered_multimap__local_iterator"></a>  unordered_multimap::local_iterator  
 值區迭代器的類型。  
  
```  
typedef T4 local_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型說明可做為值區之正向迭代器的物件。 在此將其說明為實作定義類型 `T4`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_local_iterator.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect bucket containing 'a'   
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));   
    std::cout << " [" << lit->first << ", " << lit->second << "]";   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapmappedtypea--unorderedmultimapmappedtype"></a><a name="unordered_multimap__mapped_type"></a>  unordered_multimap::mapped_type  
 與每個索引鍵關聯的對應值類型。  
  
```  
typedef Ty mapped_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是範本參數 `Ty`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_mapped_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapmaxbucketcounta--unorderedmultimapmaxbucketcount"></a><a name="unordered_multimap__max_bucket_count"></a>  unordered_multimap::max_bucket_count  
 取得 Bucket 最大數目。  
  
```  
size_type max_bucket_count() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回目前允許的最大值區數目。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_max_bucket_count.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="a-nameunorderedmultimapmaxloadfactora--unorderedmultimapmaxloadfactor"></a><a name="unordered_multimap__max_load_factor"></a>  unordered_multimap::max_load_factor  
 取得或設定每個 Bucket 最大項目數。  
  
```  
float max_load_factor() const;

 
void max_load_factor(float factor);
```  
  
### <a name="parameters"></a>參數  
 `factor`  
 新的最大載入因數。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會傳回儲存的最大載入因數。 第二個成員函式會以 `factor`取代儲存的最大載入因數。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_max_load_factor.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_bucket_count() == "   
        << c1.max_bucket_count() << std::endl;   
    std::cout << "max_load_factor() == "   
        << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_bucket_count() == 8  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_bucket_count() == 128  
max_load_factor() == 0.1  
  
```  
  
##  <a name="a-nameunorderedmultimapmaxsizea--unorderedmultimapmaxsize"></a><a name="unordered_multimap__max_size"></a>  unordered_multimap::max_size  
 取得受控制序列的大小上限。  
  
```  
size_type max_size() const;
```  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回物件可以控制之最長序列的長度。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_max_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    std::cout << "max_size() == " << c1.max_size() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
max_size() == 536870911  
```  
  
##  <a name="a-nameunorderedmultimapoperatoreqa--unorderedmultimapoperator"></a><a name="unordered_multimap__operator_eq"></a>  unordered_multimap::operator=  
 複製雜湊資料表。  
  
```  
unordered_multimap& operator=(const unordered_multimap& right);

unordered_multimap& operator=(unordered_multimap&& right);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|說明|  
|` right`|unordered_multimap 會被複製到 unordered_multimap。|  
  
### <a name="remarks"></a>備註  
 在清除並行 unordered_multimap 中的任何現有項目之後，`operator=` 會將 ` right` 的內容複製或移動至並行的 unordered_multimap。  
  
### <a name="example"></a>範例  
  
```cpp  
// unordered_multimap_operator_as.cpp  
// compile with: /EHsc  
#include <unordered_multimap>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   unordered_multimap<int, int> v1, v2, v3;  
   unordered_multimap<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="a-nameunorderedmultimappointera--unorderedmultimappointer"></a><a name="unordered_multimap__pointer"></a>  unordered_multimap::pointer  
 項目的指標類型。  
  
```  
typedef Alloc::pointer pointer;  
```  
  
### <a name="remarks"></a>備註  
 此類型所說明的物件可做為受控制序列之項目的指標。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_pointer.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::pointer p = &*it;   
        std::cout << " [" << p->first << ", " << p->second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapreferencea--unorderedmultimapreference"></a><a name="unordered_multimap__reference"></a>  unordered_multimap::reference  
 項目的參考類型。  
  
```  
typedef Alloc::reference reference;  
```  
  
### <a name="remarks"></a>備註  
 此類型所說明的物件可做為受控制序列之元素的參考。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_reference.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   
        Mymap::reference ref = *it;   
        std::cout << " [" << ref.first << ", " << ref.second << "]";   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimaprehasha--unorderedmultimaprehash"></a><a name="unordered_multimap__rehash"></a>  unordered_multimap::rehash  
 重建雜湊資料表。  
  
```  
void rehash(size_type nbuckets);
```  
  
### <a name="parameters"></a>參數  
 `nbuckets`  
 要求的值區數目。  
  
### <a name="remarks"></a>備註  
 此成員函式會將值區數目改變為至少 `nbuckets` ，並視需要重建雜湊資料表。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_rehash.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// inspect current parameters   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.10f);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
    std::cout << std::endl;   
  
// rehash and redisplay   
    c1.rehash(100);   
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;   
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;   
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 4  
  
bucket_count() == 8  
load_factor() == 0.375  
max_load_factor() == 0.1  
  
bucket_count() == 128  
load_factor() == 0.0234375  
max_load_factor() == 0.1  
```  
  
##  <a name="a-nameunorderedmultimapsizea--unorderedmultimapsize"></a><a name="unordered_multimap__size"></a>  unordered_multimap::size  
 計算元素的數目。  
  
```  
size_type size() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_size.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// clear the container and reinspect   
    c1.clear();   
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
    std::cout << std::endl;   
  
    c1.insert(Mymap::value_type('d', 4));   
    c1.insert(Mymap::value_type('e', 5));   
  
// display contents " [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    std::cout << "size == " << c1.size() << std::endl;   
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
 [c, 3] [b, 2] [a, 1]  
size == 0  
empty() == true  
  
 [e, 5] [d, 4]  
size == 2  
empty() == false  
```  
  
##  <a name="a-nameunorderedmultimapsizetypea--unorderedmultimapsizetype"></a><a name="unordered_multimap__size_type"></a>  unordered_multimap::size_type  
 兩個項目之間不帶正負號距離的類型。  
  
```  
typedef T2 size_type;  
```  
  
### <a name="remarks"></a>備註  
 此不帶正負號的整數類型所描述的物件可代表任何受控制序列的長度。 在此將其描述為已定義實作之 `T2`類型的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_size_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::size_type sz = c1.size();   
  
    std::cout << "size == " << sz << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
size == 0  
```  
  
##  <a name="a-nameunorderedmultimapswapa--unorderedmultimapswap"></a><a name="unordered_multimap__swap"></a>  unordered_multimap::swap  
 交換兩個容器的內容。  
  
```  
void swap(unordered_multimap& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 要交換的容器。  
  
### <a name="remarks"></a>備註  
 成員函式會交換 `*this` 和 `right`之間受控制的序列。 如果是 [unordered_multimap::get_allocator](#unordered_multimap__get_allocator)`() == right.get_allocator()`，它會以常數時間來執行，只會在結果是複製類型 `Tr` 預存特性物件時擲回例外狀況，並且不會使指定此兩個受控制序列中元素的任何參考、指標或迭代器失效。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    Mymap c2;   
  
    c2.insert(Mymap::value_type('d', 4));   
    c2.insert(Mymap::value_type('e', 5));   
    c2.insert(Mymap::value_type('f', 6));   
  
    c1.swap(c2);   
  
// display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapunorderedmultimapa--unorderedmultimapunorderedmultimap"></a><a name="unordered_multimap__unordered_multimap"></a>  unordered_multimap::unordered_multimap  
 建構容器物件。  
  
```  
unordered_multimap(
    const unordered_multimap& Right);

explicit unordered_multimap(
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Pred(),  
    const Allocator& Al = Alloc());

unordered_multimap(
    unordered_multimap&& Right);

unordered_multimap(
    initializer_list<Type> IList);

unordered_multimap(
    initializer_list<Type> IList,  
    size_type Bucket_count);

unordered_multimap(
    initializer_list<Type> IList,  
    size_type Bucket_count,   
    const Hash& Hash);

unordered_multimap(
    initializer_list<Type> IList,  
    size_type Bucket_count,   
    const Hash& Hash,  
    const Key& Key);

unordered_multimap(
    initializer_list<Type> IList,  
    size_type Bucket_count,   
    const Hash& Hash,  
    const Key& Key,   
    const Allocator& Al);

template <class InputIterator>  
unordered_multimap(
 InputIterator first, InputIterator last,  
    size_type Bucket_count = N0,  
    const Hash& Hash = Hash(),  
    const Comp& Comp = Pred(),  
    const Allocator& Al = Alloc());
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|`InputIterator`|迭代器類型。|  
|`Al`|要儲存的配置器物件。|  
|`Comp`|要儲存的比較函式物件。|  
|`Hash`|要儲存的雜湊函式物件。|  
|`Bucket_count`|Bucket 最小數目。|  
|`Right`|要複製的容器。|  
|`IList`|從中複製項目的 initializer_list。|  
  
### <a name="remarks"></a>備註  
 第一個建構函式指定由 `Right` 控制之序列的複本。 第二個建構函式會指定空白的受控制序列。 第三個建構函式。 透過移動 `Right` 來指定序列的複本。 第四、第五、第六、第七和第八個建構函式為成員使用 initializer_list。 第九個建構函式會插入項目值序列 `[First, Last)`。  
  
 所有建構函式也會初始化數個儲存值。 對於複製建構函式，其值是從 `Right` 取得。 否則就是：  
  
 Bucket 最小數目為引數 `Bucket_count` (如果存在)；否則其為本文所述的預設值，即由實作所定義的值 `N0`。  
  
 雜湊函式物件是引數 `Hash` (如果存在)；否則為 `Hash()`。  
  
 比對函式物件是引數 `Comp` (如果存在)；否則為 `Pred()`。  
  
 配置器物件是引數 `Al` (如果存在)；否則為 `Alloc()`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_construct.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
using namespace std;  
  
using  Mymap = unordered_multimap<char, int> ;  
int main()  
{  
    Mymap c1;  
  
    c1.insert(Mymap::value_type('a', 1));  
    c1.insert(Mymap::value_type('b', 2));  
    c1.insert(Mymap::value_type('c', 3));  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c2(8,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >());  
  
    c2.insert(Mymap::value_type('d', 4));  
    c2.insert(Mymap::value_type('e', 5));  
    c2.insert(Mymap::value_type('f', 6));  
  
    // display contents " [f 6] [e 5] [d 4]"   
    for (const auto& c : c2) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c3(c1.begin(),  
        c1.end(),  
        8,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >());  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c3) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    Mymap c4(move(c3));  
  
    // display contents " [c 3] [b 2] [a 1]"   
    for (const auto& c : c4) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Construct with an initializer_list  
    unordered_multimap<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });  
    for (const auto& c : c5) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size  
    unordered_multimap<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size and hash  
    unordered_multimap<int, char, hash<char>> c7(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },  
        4,  
        hash<char>()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size, hash, and key_equal  
    unordered_multimap<int, char, hash<char>, equal_to<char>> c8(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },  
        4,  
        hash<char>(),  
        equal_to<char>()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
  
    // Initializer_list plus size, hash, key_equal, and allocator  
    unordered_multimap<int, char, hash<char>, equal_to<char>> c9(  
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },  
        4,  
        hash<char>(),  
        equal_to<char>(),  
        allocator<pair<const char, int> >()  
    );  
  
    for (const auto& c : c1) {  
        cout << " [" << c.first << ", " << c.second << "]";  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
[a, 1] [b, 2] [c, 3] [d, 4] [e, 5] [f, 6] [a, 1] [b, 2] [c, 3] [a, 1] [b, 2] [c, 3] [5, g] [6, h] [7, i] [8, j] [a, 1] [b, 2] [c, 3] [a, 1] [b, 2] [c, 3] [a, 1] [b, 2] [c, 3] [a, 1] [b, 2] [c, 3] [c, 3] [b, 2] [a, 1]  
 [f, 6] [e, 5] [d, 4]  
 [c, 3] [b, 2] [a, 1]  
 [c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="a-nameunorderedmultimapvaluetypea--unorderedmultimapvaluetype"></a><a name="unordered_multimap__value_type"></a>  unordered_multimap::value_type  
 元素的類型。  
  
```  
typedef std::pair<const Key, Ty> value_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述受控制序列的項目。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__unordered_map__unordered_multimap_value_type.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
// add a value and reinspect   
    Mymap::key_type key = 'd';   
    Mymap::mapped_type mapped = 4;   
    Mymap::value_type val = Mymap::value_type(key, mapped);   
    c1.insert(val);   
  
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[d, 4] [c, 3] [b, 2] [a, 1]  
```  
  
## <a name="see-also"></a>另請參閱  
 [<unordered_map>](../standard-library/unordered-map.md)   
 [容器](../cpp/containers-modern-cpp.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)


