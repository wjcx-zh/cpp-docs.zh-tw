---
title: "concurrent_vector 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
dev_langs:
- C++
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: f7d3d187f69a026548a97fa9d1078651016eafe1
ms.lasthandoff: 03/17/2017

---
# <a name="concurrentvector-class"></a>concurrent_vector 類別
`concurrent_vector` 類別是一種序列容器類別，允許以隨機方式存取任何項目。 它會啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
 private details::_Concurrent_vector_base_v4;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 儲存在向量中之項目的資料型別。  
  
 `_Ax`  
 表示封裝有關配置和解除配置之記憶體的並行向量的詳細資訊的預存配置器物件的型別。 這個引數是選擇性的，而且預設值是 `allocator<``T``>`。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`allocator_type`|代表並行向量的配置器類別的類型。|  
|`const_iterator`|類型，提供隨機存取迭代器可以讀取`const`並行向量的元素。|  
|`const_pointer`|類型，提供一個指向`const`並行向量的元素。|  
|`const_reference`|提供的參考型別`const`供讀取和執行的並行向量中儲存項目`const`作業。|  
|`const_reverse_iterator`|類型，提供隨機存取迭代器可以讀取任何`const`並行向量的元素。|  
|`difference_type`|提供並行向量中的兩個項目之間的帶正負號的距離的類型。|  
|`iterator`|類型，提供可以讀取並行向量的任何元素的隨機存取迭代器。 修改使用迭代器的項目不是並行安全。|  
|`pointer`|提供並行向量中的項目之指標的類型。|  
|`reference`|類型，提供儲存在並行向量中項目的參考。|  
|`reverse_iterator`|類型，提供可以讀取反轉的並行向量的任何元素的隨機存取迭代器。 修改使用迭代器的項目不是並行安全。|  
|`size_type`|計算並行向量中的項目數的類型。|  
|`value_type`|代表並行向量中儲存的資料類型的類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[並行向量](#ctor)|多載。 建構並行向量。|  
|[~ concurrent_vector 解構函式](#dtor)|清除所有項目，並終結這個並行向量。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[assign](#assign)|多載。 清除並行向量的元素，並指派給它可以是`_N`複製的`_Item`，迭代器範圍所指定的值或 [ `_Begin`， `_End`)。 這個方法不是並行安全。|  
|[at](#at)|多載。 提供存取並行向量中指定索引處的項目。 這個方法是並行安全進行讀取作業，並同時成長，只要確定之值的向量，`_Index`小於並行向量的大小。|  
|[back](#back)|多載。 傳回的參考或`const`的最後一個參考並行向量中的項目。 如果並行向量是空的則傳回值會是未定義。 這個方法是並行安全。|  
|[begin](#begin)|多載。 傳回迭代器類型的`iterator`或`const_iterator`並行向量的開頭。 這個方法是並行安全。|  
|[capacity](#capacity)|傳回的並行向量可以成長而不必配置更多記憶體的大小上限。 這個方法是並行安全。|  
|[cbegin](#cbegin)|傳回迭代器類型的`const_iterator`並行向量的開頭。 這個方法是並行安全。|  
|[cend](#cend)|傳回迭代器類型的`const_iterator`並行向量的結尾。 這個方法是並行安全。|  
|[clear](#clear)|清除並行向量中的所有項目。 這個方法不是並行安全。|  
|[crbegin](#crbegin)|傳回迭代器類型的`const_reverse_iterator`並行向量的開頭。 這個方法是並行安全。|  
|[crend](#crend)|傳回迭代器類型的`const_reverse_iterator`並行向量的結尾。 這個方法是並行安全。|  
|[empty](#empty)|測試是否並行向量是空的時間呼叫這個方法。 這個方法是並行安全。|  
|[end](#end)|多載。 傳回迭代器類型的`iterator`或`const_iterator`並行向量的結尾。 這個方法是並行安全。|  
|[front](#front)|多載。 傳回的參考或`const`並行向量中第一個項目的參考。 如果並行向量是空的則傳回值會是未定義。 這個方法是並行安全。|  
|[get_allocator](#get_allocator)|傳回一份用來建構並行向量的配置器。 這個方法是並行安全。|  
|[grow_by](#grow_by)|多載。 增加這個並行向量`_Delta`項目。 這個方法是並行安全。|  
|[grow_to_at_least](#grow_to_at_least)|增加這個並行向量，直到其中至少有`_N`項目。 這個方法是並行安全。|  
|[max_size](#max_size)|傳回並行向量可以保存項目的數目上限。 這個方法是並行安全。|  
|[push_back](#push_back)|多載。 將指定的項目附加至並行向量的結尾。 這個方法是並行安全。|  
|[rbegin](#rbegin)|多載。 傳回迭代器類型的`reverse_iterator`或`const_reverse_iterator`並行向量的開頭。 這個方法是並行安全。|  
|[rend](#rend)|多載。 傳回迭代器類型的`reverse_iterator`或`const_reverse_iterator`並行向量的結尾。 這個方法是並行安全。|  
|[reserve](#reserve)|會配置足夠的空間大小成長並行向量`_N`而不必配置更多記憶體的更新版本。 這個方法不是並行安全。|  
|[resize](#resize)|多載。 並行向量的大小變更為所要求的大小，刪除或加入所需的項目。 這個方法不是並行安全。|  
|[shrink_to_fit](#shrink_to_fit)|壓縮來減少片段，並讓記憶體使用量最佳化的並行向量的內部表示法。 這個方法不是並行安全。|  
|[size](#size)|傳回並行向量中的項目數目。 這個方法是並行安全。|  
|[swap](#swap)|交換兩個並行向量的內容。 這個方法不是並行安全。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[operator]](#operator_at)|多載。 提供存取並行向量中指定索引處的項目。 這個方法是並行安全進行讀取作業，並同時成長，只要確定之值的向量，`_Index`小於並行向量的大小。|  
|[operator=](#operator_eq)|多載。 另一個內容指派`concurrent_vector`這個物件。 這個方法不是並行安全。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊`concurrent_vector`類別，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Concurrent_vector_base_v4`  
  
 `_Allocator_base`  
  
 `concurrent_vector`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concurrent_vector.h  
  
 **命名空間：** concurrency  
  
##  <a name="assign"></a>指派 

 清除並行向量的元素，並指派給它可以是`_N`複製的`_Item`，迭代器範圍所指定的值或 [ `_Begin`， `_End`)。 這個方法不是並行安全。  
  
```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>參數  
 `_InputIterator`  
 指定之迭代器類型。  
  
 `_N`  
 若要複製至並行向量的項目數目。  
  
 `_Item`  
 用來填滿的並行向量值參考。  
  
 `_Begin`  
 來源範圍的第一個項目的迭代器。  
  
 `_End`  
 來源範圍的最後一個元素後加迭代器。  
  
### <a name="remarks"></a>備註  
 `assign`不是並行安全。 您必須確定，沒有其他執行緒會叫用方法上的並行向量時呼叫這個方法。  
  
##  <a name="at"></a>在 

 提供存取並行向量中指定索引處的項目。 這個方法是並行安全進行讀取作業，並同時成長，只要確定之值的向量，`_Index`小於並行向量的大小。  
  
```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 要擷取之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 指定索引處的項目參考。  
  
### <a name="remarks"></a>備註  
 函式版本`at`，傳回非`const`參考不能用來從不同執行緒同時寫入項目。 不同的同步處理物件應該用於同步處理並行讀取和寫入作業的相同項目。  
  
 方法會擲回`out_of_range`如果`_Index`大於或等於並行向量的大小和`range_error`如果索引是中斷的向量部分。 如需有關如何在向量可以而損毀，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
##  <a name="back"></a>上一步 

 傳回的參考或`const`的最後一個參考並行向量中的項目。 如果並行向量是空的則傳回值會是未定義。 這個方法是並行安全。  
  
```
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>傳回值  
 參考或`const`的最後一個參考並行向量中的項目。  
  
##  <a name="begin"></a>開始 

 傳回迭代器類型的`iterator`或`const_iterator`並行向量的開頭。 這個方法是並行安全。  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`iterator`或`const_iterator`並行向量的開頭。  
  
##  <a name="capacity"></a>容量 

 傳回的並行向量可以成長而不必配置更多記憶體的大小上限。 這個方法是並行安全。  
  
```
size_type capacity() const;
```  
  
### <a name="return-value"></a>傳回值  
 並行向量可以成長而不必配置更多記憶體的大小上限。  
  
### <a name="remarks"></a>備註  
 不同於 c + + 標準程式庫`vector`、`concurrent_vector`物件不會移動現有項目，如果它配置更多記憶體。  
  
##  <a name="cbegin"></a>cbegin 

 傳回迭代器類型的`const_iterator`並行向量的開頭。 這個方法是並行安全。  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`const_iterator`並行向量的開頭。  
  
##  <a name="cend"></a>cend 

 傳回迭代器類型的`const_iterator`並行向量的結尾。 這個方法是並行安全。  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`const_iterator`並行向量的結尾。  
  
##  <a name="clear"></a>清除 

 清除並行向量中的所有項目。 這個方法不是並行安全。  
  
```
void clear();
```  
  
### <a name="remarks"></a>備註  
 `clear`不是並行安全。 您必須確定，沒有其他執行緒會叫用方法上的並行向量時呼叫這個方法。 `clear`不會釋放內部陣列。 若要釋出內部陣列，呼叫函式`shrink_to_fit`之後`clear`。  
  
##  <a name="ctor"></a>並行向量 

 建構並行向量。  
  
```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```  
  
### <a name="parameters"></a>參數  
 `M`  
 來源向量的配置器類型。  
  
 `_InputIterator`  
 輸入迭代器的類型。  
  
 `_Al`  
 搭配這個物件使用的配置器類別。  
  
 `_Vector`  
 要從中複製或移動項目的來源 `concurrent_vector` 物件。  
  
 `_N`  
 `concurrent_vector` 物件的初始容量。  
  
 `_Item`  
 建構的物件中的項目值。  
  
 `_Begin`  
 項目範圍中要複製的第一個項目位置。  
  
 `_End`  
 項目範圍之外要複製的第一個項目位置。  
  
### <a name="remarks"></a>備註  
 所有建構函式儲存配置器物件`_Al`並初始化向量。  
  
 第一個建構函式指定空的初始向量，並明確指定的配置器類型。 若要使用。  
  
 第二個和第三個建構函式會指定並行向量的複本`_Vector`。  
  
 第四個建構函式會指定移動並行向量 `_Vector`。  
  
 第五個建構函式會指定重複指定數字 ( `_N`) 的類別的預設值的項目`T`。  
  
 第六個建構函式會指定重複 ( `_N`) 值的項目`_Item`。  
  
 最後一個建構函式會指定迭代器範圍所提供的值 [ `_Begin`， `_End`)。  
  
##  <a name="dtor"></a>~ concurrent_vector 

 清除所有項目，並終結這個並行向量。  
  
```
~concurrent_vector();
```  
  
##  <a name="crbegin"></a>crbegin 

 傳回迭代器類型的`const_reverse_iterator`並行向量的開頭。 這個方法是並行安全。  
  
```
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`const_reverse_iterator`並行向量的開頭。  
  
##  <a name="crend"></a>crend 

 傳回迭代器類型的`const_reverse_iterator`並行向量的結尾。 這個方法是並行安全。  
  
```
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`const_reverse_iterator`並行向量的結尾。  
  
##  <a name="empty"></a>空白 

 測試是否並行向量是空的時間呼叫這個方法。 這個方法是並行安全。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果向量是空的呼叫函式，此時`false`否則。  
  
##  <a name="end"></a>結束 

 傳回迭代器類型的`iterator`或`const_iterator`並行向量的結尾。 這個方法是並行安全。  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`iterator`或`const_iterator`並行向量的結尾。  
  
##  <a name="front"></a>前端 

 傳回的參考或`const`並行向量中第一個項目的參考。 如果並行向量是空的則傳回值會是未定義。 這個方法是並行安全。  
  
```
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>傳回值  
 參考或`const`並行向量中第一個項目的參考。  
  
##  <a name="get_allocator"></a>get_allocator 

 傳回一份用來建構並行向量的配置器。 這個方法是並行安全。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 用來建構的配置器一份`concurrent_vector`物件。  
  
##  <a name="grow_by"></a>grow_by 

 增加這個並行向量`_Delta`項目。 這個方法是並行安全。  
  
```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```  
  
### <a name="parameters"></a>參數  
 `_Delta`  
 要附加至物件的項目數目。  
  
 `_Item`  
 要初始化新的項目與值。  
  
### <a name="return-value"></a>傳回值  
 附加至第一個項目的迭代器。  
  
### <a name="remarks"></a>備註  
 如果`_Item`未指定，新的項目是預設建構。  
  
##  <a name="grow_to_at_least"></a>grow_to_at_least 

 增加這個並行向量，直到其中至少有`_N`項目。 這個方法是並行安全。  
  
```
iterator grow_to_at_least(size_type _N);
```  
  
### <a name="parameters"></a>參數  
 `_N`  
 新的最小大小為`concurrent_vector`物件。  
  
### <a name="return-value"></a>傳回值  
 迭代器指向附加的序列的開頭或索引處的項目`_N`如果所不附加的任何項目。  
  
##  <a name="max_size"></a>max_size 

 傳回並行向量可以保存項目的數目上限。 這個方法是並行安全。  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 最大項目數`concurrent_vector`物件可以保存。  
  
##  <a name="operator_eq"></a>運算子 = 

 另一個內容指派`concurrent_vector`這個物件。 這個方法不是並行安全。  
  
```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```  
  
### <a name="parameters"></a>參數  
 `M`  
 來源向量的配置器類型。  
  
 `_Vector`  
 來源 `concurrent_vector` 物件。  
  
### <a name="return-value"></a>傳回值  
 參考`concurrent_vector`物件。  
  
##  <a name="operator_at"></a>operator] 

 提供存取並行向量中指定索引處的項目。 這個方法是並行安全進行讀取作業，並同時成長，只要確定之值的向量，`_Index`小於並行向量的大小。  
  
```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 要擷取之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 指定索引處的項目參考。  
  
### <a name="remarks"></a>備註  
 版本`operator []`，傳回非`const`參考不能用來從不同執行緒同時寫入項目。 不同的同步處理物件應該用於同步處理並行讀取和寫入作業的相同項目。  
  
 沒有繫結檢查，確保執行`_Index`是並行向量的有效索引。  
  
##  <a name="push_back"></a>push_back 

 將指定的項目附加至並行向量的結尾。 這個方法是並行安全。  
  
```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```  
  
### <a name="parameters"></a>參數  
 `_Item`  
 要附加的值。  
  
### <a name="return-value"></a>傳回值  
 附加至項目的迭代器。  
  
##  <a name="rbegin"></a>rbegin 

 傳回迭代器類型的`reverse_iterator`或`const_reverse_iterator`並行向量的開頭。 這個方法是並行安全。  
  
```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`reverse_iterator`或`const_reverse_iterator`並行向量的開頭。  
  
##  <a name="rend"></a>rend 

 傳回迭代器類型的`reverse_iterator`或`const_reverse_iterator`並行向量的結尾。 這個方法是並行安全。  
  
```
reverse_iterator rend();

const_reverse_iterator rend() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`reverse_iterator`或`const_reverse_iterator`並行向量的結尾。  
  
##  <a name="reserve"></a>保留 

 會配置足夠的空間大小成長並行向量`_N`而不必配置更多記憶體的更新版本。 這個方法不是並行安全。  
  
```
void reserve(size_type _N);
```  
  
### <a name="parameters"></a>參數  
 `_N`  
 要保留的空間元素數目。  
  
### <a name="remarks"></a>備註  
 `reserve`不是並行安全。 您必須確定，沒有其他執行緒會叫用方法上的並行向量時呼叫這個方法。 在方法傳回後的並行向量的容量可能大於所要求的保留。  
  
##  <a name="resize"></a>調整大小 

 並行向量的大小變更為所要求的大小，刪除或加入所需的項目。 這個方法不是並行安全。  
  
```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```  
  
### <a name="parameters"></a>參數  
 `_N`  
 並行向量的新大小。  
  
 `val`  
 如果新的大小大於原始大小，則會將新項目的值加入至向量。 如果省略此值，新的物件會指定其類型的預設值。  
  
### <a name="remarks"></a>備註  
 如果容器的大小小於所要求的大小，項目會加入至向量，直到達到所要求的大小。 如果容器大小大於所要求的大小，最接近容器結尾的項目會刪除之前容器達到大小`_N`。 如果容器現在的大小與所要求的大小相同，則不會採取任何動作。  
  
 `resize`不是並行安全。 您必須確定，沒有其他執行緒會叫用方法上的並行向量時呼叫這個方法。  
  
##  <a name="shrink_to_fit"></a>shrink_to_fit 

 壓縮來減少片段，並讓記憶體使用量最佳化的並行向量的內部表示法。 這個方法不是並行安全。  
  
```
void shrink_to_fit();
```  
  
### <a name="remarks"></a>備註  
 這個方法會在內部重新配置記憶體移動項目，使所有迭代器無效。 `shrink_to_fit`不是並行安全。 您必須確定，沒有其他執行緒會叫用方法上的並行向量時呼叫此函式。  
  
##  <a name="size"></a>大小 

 傳回並行向量中的項目數目。 這個方法是並行安全。  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>傳回值  
 在此的項目數`concurrent_vector`物件。  
  
### <a name="remarks"></a>備註  
 傳回的大小一定會包含所有的項目所呼叫函式附加`push_back`，或成長之前叫用這個方法已完成的作業。 不過，它也可以包含已配置的項目但仍在並行呼叫的任何成長方法建構。  
  
##  <a name="swap"></a>交換 

 交換兩個並行向量的內容。 這個方法不是並行安全。  
  
```
void swap(concurrent_vector& _Vector);
```  
  
### <a name="parameters"></a>參數  
 `_Vector`  
 `concurrent_vector`來交換內容的物件。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)




