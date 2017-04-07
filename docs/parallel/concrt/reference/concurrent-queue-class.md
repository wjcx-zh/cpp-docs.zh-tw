---
title: "concurrent_queue 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
dev_langs:
- C++
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
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
ms.openlocfilehash: d2af8483f38a14454e3aa1aecf28864bab1c6a1a
ms.lasthandoff: 03/17/2017

---
# <a name="concurrentqueue-class"></a>concurrent_queue 類別
`concurrent_queue` 類別是一種序列容器類別，允許以先進先出的方式存取其項目。 它會啟用一組有限的並行安全作業，例如 `push` 和 `try_pop` 等。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 儲存在佇列中之項目的資料型別。  
  
 `_Ax`  
 表示封裝有關配置和解除配置的記憶體，此並行佇列的詳細資訊的預存配置器物件的型別。 這個引數是選擇性的，而且預設值是 `allocator<``T``>`。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`allocator_type`|代表並行佇列之配置器類別的類型。|  
|`const_iterator`|表示非執行緒安全的型別`const`迭代器並行佇列中的項目。|  
|`const_reference`|提供的參考型別`const`項目儲存在並行佇列進行讀取和執行`const`作業。|  
|`difference_type`|提供並行佇列中的兩個項目之間的帶正負號的距離的類型。|  
|`iterator`|並行佇列中的項目代表非執行緒安全的迭代器的類型。|  
|`reference`|提供參考文件儲存在並行佇列中的項目類型。|  
|`size_type`|計算並行佇列中的項目數的類型。|  
|`value_type`|表示儲存在並行佇列中的資料類型的類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[concurrent_queue](#ctor)|多載。 建構並行佇列。|  
|[~ concurrent_queue 解構函式](#dtor)|終結並行佇列。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[clear](#clear)|清除並行佇列，終結任何目前項目加入佇列。 這個方法不是並行安全。|  
|[empty](#empty)|測試如果並行佇列是空的此時會呼叫這個方法。 這個方法是並行安全。|  
|[get_allocator](#get_allocator)|傳回一份用來建構並行佇列之配置器。 這個方法是並行安全。|  
|[push](#push)|多載。 將位於尾端的項目，並行佇列的佇列。 這個方法是並行安全。|  
|[try_pop](#try_pop)|如果有的話，請清除佇列中的項目。 這個方法是並行安全。|  
|[unsafe_begin](#unsafe_begin)|多載。 傳回迭代器類型的`iterator`或`const_iterator`並行佇列的開頭。 這個方法不是並行安全。|  
|[unsafe_end](#unsafe_end)|多載。 傳回迭代器類型的`iterator`或`const_iterator`並行佇列的結尾。 這個方法不是並行安全。|  
|[unsafe_size](#unsafe_size)|傳回佇列中的項目數目。 這個方法不是並行安全。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `concurrent_queue`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concurrent_queue.h  
  
 **命名空間：** concurrency  
  
##  <a name="clear"></a>清除 

 清除並行佇列，終結任何目前項目加入佇列。 這個方法不是並行安全。  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_queue 

 建構並行佇列。  
  
```
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```  
  
### <a name="parameters"></a>參數  
 `_InputIterator`  
 指定的值範圍的輸入迭代器類型。  
  
 `_Al`  
 搭配這個物件使用的配置器類別。  
  
 `_OtherQ`  
 要從中複製或移動項目的來源 `concurrent_queue` 物件。  
  
 `_Begin`  
 項目範圍中要複製的第一個項目位置。  
  
 `_End`  
 項目範圍之外要複製的第一個項目位置。  
  
### <a name="remarks"></a>備註  
 所有建構函式儲存配置器物件`_Al`和初始化佇列。  
  
 第一個建構函式指定空的初始佇列，並明確指定要使用的配置器類型。  
  
 第二個建構函式會指定並行佇列一份`_OtherQ`。  
  
 第三個建構函式會指定並行佇列 `_OtherQ` 的移動作業。  
  
 第四個建構函式會指定迭代器範圍所提供的值 [ `_Begin`， `_End`)。  
  
##  <a name="dtor"></a>~ concurrent_queue 

 終結並行佇列。  
  
```
~concurrent_queue();
```  
  
##  <a name="empty"></a>空白 

 測試如果並行佇列是空的此時會呼叫這個方法。 這個方法是並行安全。  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>傳回值  
 `true`如果並行佇列是空的我們討論了，此時`false`否則。  
  
### <a name="remarks"></a>備註  
 這個方法時並行安全方面方法的呼叫`push`， `try_pop`，和`empty`，它會檢查由呼叫執行緒的時間，傳回的值可能會不正確。  
  
##  <a name="get_allocator"></a>get_allocator 

 傳回一份用來建構並行佇列之配置器。 這個方法是並行安全。  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>傳回值  
 用來建構並行佇列之配置器的複本。  
  
##  <a name="push"></a>推播 

 將位於尾端的項目，並行佇列的佇列。 這個方法是並行安全。  
  
```
void push(const T& _Src);

void push(T&& _Src);
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
 要加入佇列的項目。  
  
### <a name="remarks"></a>備註  
 `push`是並行安全方面方法的呼叫`push`， `try_pop`，和`empty`。  
  
##  <a name="try_pop"></a>try_pop 

 如果有的話，請清除佇列中的項目。 這個方法是並行安全。  
  
```
bool try_pop(T& _Dest);
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 參考的位置來儲存從佇列中清除的項目。  
  
### <a name="return-value"></a>傳回值  
 `true`如果項目已成功地從佇列中清除，`false`否則。  
  
### <a name="remarks"></a>備註  
 如果已成功地從佇列中清除，項目參數`_Dest`接收從佇列中清除的值，保留在佇列中的原始值遭到破壞，而此函數會傳回`true`。 如果沒有任何項目來清除佇列，則此函數會傳回`false`而封鎖的內容`_Dest`是未定義的參數。  
  
 `try_pop`是並行安全方面方法的呼叫`push`， `try_pop`，和`empty`。  
  
##  <a name="unsafe_begin"></a>unsafe_begin 

 傳回迭代器類型的`iterator`或`const_iterator`並行佇列的開頭。 這個方法不是並行安全。  
  
```
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`iterator`或`const_iterator`並行佇列物件的開頭。  
  
### <a name="remarks"></a>備註  
 迭代器的`concurrent_queue`類別主要是供偵錯，執行速度很慢，以及反覆項目不是並行安全相對於其他佇列作業。  
  
##  <a name="unsafe_end"></a>unsafe_end 

 傳回迭代器類型的`iterator`或`const_iterator`並行佇列的結尾。 這個方法不是並行安全。  
  
```
iterator unsafe_end();

const_iterator unsafe_end() const;
```  
  
### <a name="return-value"></a>傳回值  
 迭代器類型的`iterator`或`const_iterator`並行佇列的結尾。  
  
### <a name="remarks"></a>備註  
 迭代器的`concurrent_queue`類別主要是供偵錯，執行速度很慢，以及反覆項目不是並行安全相對於其他佇列作業。  
  
##  <a name="unsafe_size"></a>unsafe_size 

 傳回佇列中的項目數目。 這個方法不是並行安全。  
  
```
size_type unsafe_size() const;
```  
  
### <a name="return-value"></a>傳回值  
 並行佇列的大小。  
  
### <a name="remarks"></a>備註  
 `unsafe_size`不是並行安全，而且可以產生不正確的結果，如果呼叫方法的呼叫與`push`， `try_pop`，和`empty`。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

