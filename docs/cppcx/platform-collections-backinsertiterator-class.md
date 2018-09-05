---
title: Platform::Collections::BackInsertIterator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
dev_langs:
- C++
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c0678dbb78aaa115c0c4f3120a8bc0d74bf1c65
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760727"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator 類別
代表將元素插入 (而不是覆寫) 序列集合後端的迭代器。  
  
## <a name="syntax"></a>語法  
  
```  
template <typename T>  
class BackInsertIterator : 
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 目前集合中的項目類型。  
  
### <a name="remarks"></a>備註  
 BackInsertIterator 類別實作 [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md)所需的規則。  
  
### <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[BackInsertIterator::BackInsertIterator](#ctor)|初始化 BackInsertIterator 類別的新執行個體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[BackInsertIterator::operator* 運算子](#operator-dereference)|擷取目前 BackInsertIterator 的參考。|  
|[BackInsertIterator::operator++ 運算子](#operator-increment)|傳回目前 BackInsertIterator 的參考。 迭代器是未修改的。|  
|[BackInsertIterator::operator= 運算子](#operator-assign)|將指定的物件附加至目前循序集合的結尾。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `BackInsertIterator`  
  
### <a name="requirements"></a>需求  
 **標頭：** collection.h  
  
 **命名空間：** Platform::Collections  
  
---
## <a name="ctor"></a>  Backinsertiterator:: Backinsertiterator 建構函式
初始化 `BackInsertIterator` 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
#### <a name="parameters"></a>參數  
 `v`  
 IVector\<T > 物件。  
  
### <a name="remarks"></a>備註  
 `BackInsertIterator` 在參數 `v` 所指定的物件的最後一個元素之後插入元素。  
 
## <a name="operator-assign"></a>  Backinsertiterator:: Operator = 運算子
將指定的物件附加至目前循序集合的結尾。  
  
## <a name="syntax"></a>語法  
  
```    
BackInsertIterator& operator=( const T& t);  
```  
  
#### <a name="parameters"></a>參數  
 `t`  
 要附加至目前集合的物件。  
  
### <a name="return-value"></a>傳回值  
 目前 BackInsertIterator 的參考。  

## <a name="operator-dereference"></a>  Backinsertiterator:: Operator * 運算子
擷取目前 BackInsertIterator 的參考。  
  
## <a name="syntax"></a>語法  
  
```  
BackInsertIterator& operator*();  
```  
  
### <a name="return-value"></a>傳回值  
 目前 BackInsertIterator 的參考。  
  
### <a name="remarks"></a>備註  
 這個運算子會傳回目前 BackInsertIterator 的參考，不是目前集合中任何項目的參考。  
 
## <a name="operator-increment"></a>  Backinsertiterator:: Operator + + 運算子
傳回目前 BackInsertIterator 的參考。 迭代器是未修改的。  
  
## <a name="syntax"></a>語法  
  
``` 
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(int);  
```  
  
### <a name="return-value"></a>傳回值  
 目前 BackInsertIterator 的參考。  
  
### <a name="remarks"></a>備註  
 根據設計，第一個語法範例會對目前 BackInsertIterator 前置遞增，而第二個語法則是對目前 BackInsertIterator 後置遞增。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。  
  
 不過，這個運算子不會實際修改 BackInsertIterator。 而是傳回未修改之目前迭代器的參考。 這是相同的行為[運算子 *](#dereference-operator)。  
  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)