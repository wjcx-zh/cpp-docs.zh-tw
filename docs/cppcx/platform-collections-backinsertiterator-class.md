---
title: Platform::Collections::BackInsertIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: 56393fd522ecd0e2f161dfa5b9fe8230563c0f65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223482"
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

*T*<br/>
目前集合中的項目類型。

### <a name="remarks"></a>備註

BackInsertIterator 類別實作 [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md)所需的規則。

### <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[BackInsertIterator：： BackInsertIterator](#ctor)|初始化 BackInsertIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|Name|說明|
|----------|-----------------|
|[BackInsertIterator：： operator * 運算子](#operator-dereference)|擷取目前 BackInsertIterator 的參考。|
|[BackInsertIterator：： operator + + 運算子](#operator-increment)|傳回目前 BackInsertIterator 的參考。 迭代器是未修改的。|
|[BackInsertIterator::operator= 運算子](#operator-assign)|將指定的物件附加至目前循序集合的結尾。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`BackInsertIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a>BackInsertIterator：： BackInsertIterator 函式

初始化 `BackInsertIterator` 類別的新執行個體。

## <a name="syntax"></a>語法

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>參數

*&*<br/>
IVector \<T> 物件。

### <a name="remarks"></a>備註

`BackInsertIterator` 在參數 `v` 所指定的物件的最後一個元素之後插入元素。

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a>BackInsertIterator：： operator = 運算子

將指定的物件附加至目前循序集合的結尾。

## <a name="syntax"></a>語法

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>參數

*而已*<br/>
要附加至目前集合的物件。

### <a name="return-value"></a>傳回值

目前 BackInsertIterator 的參考。

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a>BackInsertIterator：： operator * 運算子

擷取目前 BackInsertIterator 的參考。

## <a name="syntax"></a>語法

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>傳回值

目前 BackInsertIterator 的參考。

### <a name="remarks"></a>備註

這個運算子會傳回目前 BackInsertIterator 的參考，不是目前集合中任何項目的參考。

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a>BackInsertIterator：： operator + + 運算子

傳回目前 BackInsertIterator 的參考。 迭代器是未修改的。

## <a name="syntax"></a>語法

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>傳回值

目前 BackInsertIterator 的參考。

### <a name="remarks"></a>備註

根據設計，第一個語法範例會對目前 BackInsertIterator 前置遞增，而第二個語法則是對目前 BackInsertIterator 後置遞增。 **`int`** 第二個語法中的類型表示遞增後作業，而不是實際的整數運算元。

不過，這個運算子不會實際修改 BackInsertIterator。 而是傳回未修改之目前迭代器的參考。 這個行為與[operator *](#operator-dereference)相同。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
