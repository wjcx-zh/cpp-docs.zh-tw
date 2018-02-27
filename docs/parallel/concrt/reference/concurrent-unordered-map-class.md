---
title: "concurrent_unordered_map 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d37feb147cc0604081479bfae0afca933c251bc8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map 類別
`concurrent_unordered_map` 類別是一種並行安全容器，可控制 `std::pair<const K, _Element_type>` 類型項目的不同長度序列。 序列的表示方式導致啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。  
  
## <a name="syntax"></a>語法  
  
```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
 typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
 details::_Hash_compare<K,
    _Hasher,
 key_equality>,
    _Allocator_type,
 false>>;
```  
  
#### <a name="parameters"></a>參數  
 `K`  
 索引鍵類型。  
  
 `_Element_type`  
 對應的類型。  
  
 `_Hasher`  
 雜湊函式物件類型。 這個引數是選擇性的，而且預設值是 `std::hash<K>`。  
  
 `key_equality`  
 相等比較函式物件類型。 這個引數是選擇性的，而且預設值是 `std::equal_to<K>`。  
  
 `_Allocator_type`  
 表示封裝有關配置和解除配置的記憶體供並行的未排序對應的詳細資訊的預存配置器物件的型別。 這個引數是選擇性，而且預設值是`std::allocator<std::pair<K`， `_Element_type>>`。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`allocator_type`|管理儲存體的配置器類型。|  
|`const_iterator`|用於受控制序列的常數迭代器類型。|  
|`const_local_iterator`|用於受控制序列的常數 Bucket 迭代器類型。|  
|`const_pointer`|項目的常數指標類型。|  
|`const_reference`|項目的常數參考類型。|  
|`difference_type`|兩個項目之間帶正負號距離的類型。|  
|`hasher`|雜湊函式的類型。|  
|`iterator`|受控制序列之迭代器的類型。|  
|`key_equal`|比較函式的類型。|  
|`key_type`|排序索引鍵的類型。|  
|`local_iterator`|用於受控制序列的 Bucket 迭代器類型。|  
|`mapped_type`|與每個索引鍵關聯的對應值類型。|  
|`pointer`|項目的指標類型。|  
|`reference`|項目的參考類型。|  
|`size_type`|兩個項目之間不帶正負號距離的類型。|  
|`value_type`|元素的類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[concurrent_unordered_map](#ctor)|多載。 建構並行的未排序的對應。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[at](#at)|多載。 尋找的項目中`concurrent_unordered_map`具有指定索引鍵的值... 這個方法是並行安全。|  
|[hash_function](#hash_function)|取得儲存的雜湊函式物件。|  
|[insert](#insert)|多載。 將項目來加入`concurrent_unordered_map`物件。|  
|[key_eq](#key_eq)|取得預存的相等比較函式物件。|  
|[swap](#swap)|交換兩個內容`concurrent_unordered_map`物件。 這個方法不是並行安全。|  
|[unsafe_erase](#unsafe_erase)|多載。 移除項目從`concurrent_unordered_map`位於指定位置。 這個方法不是並行安全。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator[]](#operator_at)|多載。 尋找或插入具有指定索引鍵的項目。 這個方法是並行安全。|  
|[operator=](#operator_eq)|多載。 另一個內容指派`concurrent_unordered_map`給這一個物件。 這個方法不是並行安全。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊`concurrent_unordered_map`類別，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>需求  
 **標頭：** concurrent_unordered_map.h  
  
 **命名空間：** concurrency  
  
##  <a name="at"></a> 在 

 尋找的項目中`concurrent_unordered_map`具有指定索引鍵的值... 這個方法是並行安全。  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>參數  
 `KVal`  
 要尋找的索引鍵值。  
  
### <a name="return-value"></a>傳回值  
 所找到項目之資料值的參考。  
  
### <a name="remarks"></a>備註  
 如果找不到引數索引鍵值，函式會擲回 `out_of_range` 類別的物件。  
  
##  <a name="begin"></a> 開始 

 傳回迭代器指向並行容器中的第一個項目。 這個方法是安全的並行存取。  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>傳回值  
 並行容器中第一個項目的迭代器。  
  
##  <a name="cbegin"></a> cbegin 

 傳回指向並行容器中的第一個元素的 const 迭代器。 這個方法是安全的並行存取。  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 並行容器中第一個項目的常數迭代器。  
  
##  <a name="cend"></a> cend 

 傳回指向下一個位置定址，並行容器中的最後一個元素的 const 迭代器。 這個方法是安全的並行存取。  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 Const 迭代器之後，並行容器中的最後一個元素的位置。  
  
##  <a name="clear"></a> 清除 

 清除並行容器中的所有項目。 此函式不是安全的並行存取。  
  
```
void clear();
```  
  
##  <a name="ctor"></a> concurrent_unordered_map 

 建構並行的未排序的對應。  
  
```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>參數  
 `_Iterator`  
 輸入迭代器的類型。  
  
 `_Number_of_buckets`  
 這個未排序對應的 Bucket 初始數量。  
  
 `_Hasher`  
 這個未排序對應的雜湊函式。  
  
 `key_equality`  
 這個未排序對應的相等比較函式。  
  
 `_Allocator`  
 這個未排序對應的配置器。  
  
 `_Begin`  
 要複製的元素範圍中第一個元素的位置。  
  
 `_End`  
 超出要複製之元素範圍的第一個元素的位置。  
  
 `_Umap`  
 要從中複製或移動項目的來源 `concurrent_unordered_map` 物件。  
  
### <a name="remarks"></a>備註  
 所有的建構函式都會儲存配置器物件 `_Allocator` 並初始化未排序的對應。  
  
 第一個建構函式會指定空的初始對應，並明確指定要使用的 Bucket、雜湊函式、相等函式和配置器類型的數目。  
  
 第二個建構函式會指定未排序對應的配置器。  
  
 第三個建構函式指定的值提供的迭代器範圍 [ `_Begin`， `_End`)。  
  
 第四個和第五個建構函式會指定並行未排序之對應 `_Umap` 的複製作業。  
  
 最後一個建構函式會指定並行未排序之對應 `_Umap` 的移動作業。  
  
##  <a name="count"></a> 計數 

 計算符合指定的索引鍵的項目數目。 此函式是安全的並行存取。  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>參數  
 `KVal`  
 要搜尋的索引鍵。  
  
### <a name="return-value"></a>傳回值  
 次數的索引鍵出現在容器的次數。  
  
##  <a name="empty"></a> 空白 

 測試項目是否不存在。 這個方法是安全的並行存取。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 `true` 並行容器是空的如果`false`否則。  
  
### <a name="remarks"></a>備註  
 如果並行插入存在並行容器空白可能會變更之後立即呼叫此函式，即使讀取傳回的值之前。  
  
##  <a name="end"></a> 結束 

 傳回指向下一個位置定址，並行容器中的最後一個元素的迭代器。 這個方法是安全的並行存取。  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器之後，並行容器中的最後一個元素的位置。  
  
##  <a name="equal_range"></a> equal_range 

 尋找符合指定之索引鍵的範圍。 此函式是安全的並行存取。  
  
```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```  
  
### <a name="parameters"></a>參數  
 `KVal`  
 要搜尋的索引鍵的值。  
  
### <a name="return-value"></a>傳回值  
 A[組](http://msdn.microsoft.com/en-us/c5a37023-d939-4eb2-ae24-ce8e0cd4505d)其中的第一個元素是開頭的迭代器，而第二個項目，則範圍結尾的迭代器。  
  
### <a name="remarks"></a>備註  
 它有可能會造成額外的金鑰之後開始的迭代器，以及結尾迭代器之前插入的並行插入。  
  
##  <a name="find"></a> 尋找 

 尋找符合指定之索引鍵的元素。 此函式是安全的並行存取。  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>參數  
 `KVal`  
 要搜尋的索引鍵的值。  
  
### <a name="return-value"></a>傳回值  
 迭代器指向的位置比對提供的索引鍵的第一個元素或迭代器`end()`如果沒有這類元素存在。  
  
##  <a name="get_allocator"></a> get_allocator 

 傳回這個並行容器的預存配置器物件。 這個方法是安全的並行存取。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 這個並行容器預存配置器物件。  
  
##  <a name="hash_function"></a> hash_function 

 取得儲存的雜湊函式物件。  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>傳回值  
 儲存的雜湊函式物件。  
  
##  <a name="insert"></a> 插入 

 將項目來加入`concurrent_unordered_map`物件。  
  
```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```  
  
### <a name="parameters"></a>參數  
 `_Iterator`  
 用來插入的迭代器類型。  
  
 `V`  
 值插入對應的類型。  
  
 `value`  
 要插入的值。  
  
 `_Where`  
 要搜尋插入點的起始位置。  
  
 `first`  
 要插入之範圍的開頭。  
  
 `last`  
 要插入之範圍的結尾。  
  
### <a name="return-value"></a>傳回值  
 迭代器和布林值，包含一組。 請參閱 < 備註 > 一節，如需詳細資訊。  
  
### <a name="remarks"></a>備註  
 第一個成員函式來判斷其索引鍵具有對等順序之序列中是否存在的項目 X `value`。 如果不是，建立這類項目 X，並且將它與初始化`value`。 此函數接著會判斷迭代器`where`X，其中指定。如果發生插入，則此函數會傳回`std::pair(where, true)`。 否則它會傳回 `std::pair(where, false)`。  
  
 第二個成員函式會傳回 insert ( `value`)，並使用`_Where`做為要搜尋插入點的受控制序列內的起始位置。  
  
 第三個成員函式會將元素值序列插入從範圍 [ `first`， `last`)。  
  
 最後兩個成員函式的行為與前兩個相同，不過 `value` 是用來建構插入的值。  
  
##  <a name="key_eq"></a> key_eq 

 取得預存的相等比較函式物件。  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>傳回值  
 預存的相等比較函式物件。  
  
##  <a name="load_factor"></a> load_factor 

 計算並傳回目前的負載因數的容器。 載入因數是除以貯體數目的容器中的項目數。  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>傳回值  
 容器載入因數。  
  
##  <a name="max_load_factor"></a> max_load_factor 

 取得或設定容器的最大載入因數。 最大載入因數可以先貯體中容器擴大其內部資料表是最大數目的項目。  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>參數  
 `_Newmax`  
  
### <a name="return-value"></a>傳回值  
 第一個成員函式會傳回儲存的最大載入因數。 第二個成員函式沒有傳回值，但會擲回[out_of_range](../../../standard-library/out-of-range-class.md)如果提供的負載因數是無效的例外狀況...  
  
##  <a name="max_size"></a> max_size 

 傳回並行容器，取決於配置的大小上限。 這個方法是安全的並行存取。  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 可以插入到這個並行容器的項目數目上限。  
  
### <a name="remarks"></a>備註  
 此上限值實際上可能會高於什麼容器可以實際保存。  
  
##  <a name="operator_at"></a> operator] 

 尋找或插入具有指定索引鍵的項目。 這個方法是並行安全。  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>參數  
 `KVal`  
 索引鍵值  
  
 尋找或插入。  
  
### <a name="return-value"></a>傳回值  
 找到或插入項目的資料值的參考。  
  
### <a name="remarks"></a>備註  
 如果找不到引數索引鍵值，則將它與資料類型的預設值一起插入。  
  
 `operator[]` 可用來將項目插入對應`m`使用`m[key] = DataValue;`，其中`DataValue`值`mapped_type`索引鍵的值是項目的`key`。  
  
 當使用 `operator[]` 插入項目時，傳回的參考不會指出插入是變更預先存在的項目，還是建立新的項目。 成員函式`find`和[插入](#insert)可用來判斷是否具有指定索引鍵的項目已經在插入之前存在。  
  
##  <a name="operator_eq"></a> 運算子 = 

 另一個內容指派`concurrent_unordered_map`給這一個物件。 這個方法不是並行安全。  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>參數  
 `_Umap`  
 來源 `concurrent_unordered_map` 物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`concurrent_unordered_map`物件。  
  
### <a name="remarks"></a>備註  
 在清除任何現有的項目之後，並行向量 `operator=` 會將 `_Umap` 內容複製或移動至並行向量。  
  
##  <a name="rehash"></a> rehash 

 重建雜湊資料表。  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>參數  
 `_Buckets`  
 所需的貯體數目。  
  
### <a name="remarks"></a>備註  
 此成員函式會將值區數目改變為至少 `_Buckets` ，並視需要重建雜湊資料表。 Bucket 的數目必須是 2 的乘冪。 如果不 2 的乘冪，它會無條件進位到下一個最大 2 的乘冪。  
  
 它會擲回[out_of_range](../../../standard-library/out-of-range-class.md)例外狀況，如果是無效的值區數目 （0 或大於 bucket 最大數目）。  
  
##  <a name="size"></a> 大小 

 傳回這個並行容器中的項目數目。 這個方法是安全的並行存取。  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 容器中的項目數目。  
  
### <a name="remarks"></a>備註  
 有並行插入存在時，並行容器中的項目數可能會在呼叫這個函式之後立即變更，甚至會是在尚未讀取傳回值的情況下。  
  
##  <a name="swap"></a> 交換 

 交換兩個內容`concurrent_unordered_map`物件。 這個方法不是並行安全。  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>參數  
 `_Umap`  
 要交換的 `concurrent_unordered_map` 物件。  
  
##  <a name="unsafe_begin"></a> unsafe_begin 

 傳回特定值區的此容器中的第一個元素的迭代器。  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>參數  
 `_Bucket`  
 值區的索引。  
  
### <a name="return-value"></a>傳回值  
 迭代器，指向 bucket 的開頭。  
  
##  <a name="unsafe_bucket"></a> unsafe_bucket 

 傳回特定的索引鍵對應至這個容器中的值區索引。  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>參數  
 `KVal`  
 要搜尋的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 此容器中的索引鍵的值區索引。  
  
##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count 

 在此容器中傳回目前的 bucket 數目。  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>傳回值  
 目前此容器中的貯體數目。  
  
##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size 

 傳回這個容器的特定值區中的項目數目。  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>參數  
 `_Bucket`  
 若要搜尋的值區。  
  
### <a name="return-value"></a>傳回值  
 目前此容器中的貯體數目。  
  
##  <a name="unsafe_cbegin"></a> unsafe_cbegin 

 傳回特定值區的此容器中的第一個元素的迭代器。  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>參數  
 `_Bucket`  
 值區的索引。  
  
### <a name="return-value"></a>傳回值  
 迭代器，指向 bucket 的開頭。  
  
##  <a name="unsafe_cend"></a> unsafe_cend 

 傳回迭代器定址的下一個特定的貯體中的最後一個元素的位置。  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>參數  
 `_Bucket`  
 值區的索引。  
  
### <a name="return-value"></a>傳回值  
 迭代器，指向 bucket 的開頭。  
  
##  <a name="unsafe_end"></a> unsafe_end 

 傳回特定值區的此容器中的最後一個元素的迭代器。  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>參數  
 `_Bucket`  
 值區的索引。  
  
### <a name="return-value"></a>傳回值  
 指向值區的結尾迭代器。  
  
##  <a name="unsafe_erase"></a> unsafe_erase 

 移除項目從`concurrent_unordered_map`位於指定位置。 這個方法不是並行安全。  
  
```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```  
  
### <a name="parameters"></a>參數  
 `_Where`  
 若要清除從迭代器位置。  
  
 `_Begin`  
 項目範圍中要清除的第一個項目的位置。  
  
 `_End`  
 超出要清除之項目範圍的第一個項目的位置。  
  
 `KVal`  
 要清除的索引鍵的值。  
  
### <a name="return-value"></a>傳回值  
 前兩個成員函式會傳回指定任何移除的項目之外剩餘的第一個元素的迭代器或`concurrent_unordered_map::end`（)，如果沒有這類元素存在。 第三個成員函式會傳回它會移除的項目數目。  
  
### <a name="remarks"></a>備註  
 第一個成員函式會移除 `_Where` 所指向之受控制序列中的項目。 第二個成員函式範圍中移除的項目 [ `_Begin`， `_End`)。  
  
 第三個成員函式來分隔範圍中移除的項目`concurrent_unordered_map::equal_range`(KVal)。  
  
##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count 

 在這個容器中傳回值區的數目上限。  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>傳回值  
 此容器中的值區數目上限。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)



