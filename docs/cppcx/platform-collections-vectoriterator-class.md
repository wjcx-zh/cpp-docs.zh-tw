---
title: 2&gt;platform::collections::vectoriterator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
dev_langs:
- C++
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20da45d6161f76043c3d06f027192726c3520f44
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102547"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator 類別

衍生自 Windows 執行階段 IVector 介面的物件提供標準樣板程式庫迭代器。

VectorIterator 會儲存類型 VectorProxy 項目的 proxy 迭代器\<T >。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

## <a name="syntax"></a>語法

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>參數

*T*<br/>
VectorIterator 樣板類別的 typename。

### <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`difference_type`|指標差異 (ptrdiff_t)。|
|`iterator_category`|隨機存取迭代器的分類 (::std::random_access_iterator_tag)。|
|`pointer`|內部類型 Platform::Collections::Details::VectorProxy 指標\<T >，也就是 VectorIterator 實作所需。|
|`reference`|內部類型 Platform::Collections::Details::VectorProxy 參考\<T >，也就是 VectorIterator 實作所需。|
|`value_type`|`T` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[VectorIterator::VectorIterator](#ctor)|初始化 VectorIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[VectorIterator::operator- 運算子](#operator-minus)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|
|[VectorIterator::operator-- 運算子](#operator-decrement)|遞減目前 VectorIterator。|
|[VectorIterator::operator!= 運算子](#operator-inequality)|指出目前 VectorIterator 是否不等於指定的 VectorIterator。|
|[VectorIterator::operator* 運算子](#operator-dereference)|擷取目前 VectorIterator 指定之元素的參考。|
|[VectorIterator::operator\[\]](#operator-at)|擷取從目前 VectorIterator 開始指定偏移的元素的參考。|
|[VectorIterator::operator+ 運算子](#operator-plus)|傳回 VectorIterator ，參考從指定的 VectorIterator 開始指定位移的項目。|
|[VectorIterator::operator++ 運算子](#operator-increment)|遞增目前 VectorIterator。|
|[VectorIterator::operator+= 運算子](#operator-plus-assign)|依指定的位移值遞增目前 VectorIterator。|
|[VectorIterator::operator< 運算子](#operator-less-than)|指出目前 VectorIterator 是否小於指定的 VectorIterator。|
|[Vectoriterator:: Operator\<= 運算子](#operator-less-than-or-equals)|指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。|
|[VectorIterator::operator-= 運算子](#operator-subtract-assign)|依指定的位移遞減目前 VectorIterator。|
|[VectorIterator::operator== 運算子](#operator-equality)|指出目前 VectorIterator 是否等於指定的 VectorIterator。|
|[VectorIterator::operator> 運算子](#operator-greater-than)|指出目前 VectorIterator 是否大於指定的 VectorIterator。|
|[VectorIterator::operator-> 運算子](#operator-arrow)|擷取目前 VectorIterator 參考的元素的位址。|
|[VectorIterator::operator>= 運算子](#operator-greater-than-or-equal)|指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。|

## <a name="inheritance-hierarchy"></a>繼承階層

`VectorIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="operator-arrow"></a>  Vectoriterator:: Operator-&gt;運算子

擷取目前 VectorIterator 參考的元素的位址。

### <a name="syntax"></a>語法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>傳回值

目前 VectorIterator 參考的項目值。

傳回值的類型是實作這個運算子所需之未指定的內部類型。

## <a name="operator-decrement"></a>  Vectoriterator:: Operator-運算子

遞減目前 VectorIterator。

### <a name="syntax"></a>語法

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>傳回值

第一種語法會先遞減，再傳回目前的 VectorIterator。 第二種語法先傳回目前 VectorIterator 的複本，再遞減目前的 VectorIterator。

### <a name="remarks"></a>備註

第一種 VectorIterator 語法會預先遞減目前的 VectorIterator。

第二種語法會後置遞減目前的 VectorIterator。 `int`第二個語法中的類型表示後置遞減作業，而不是實際的整數運算元。

## <a name="operator-dereference"></a>  Vectoriterator:: Operator\*運算子

擷取目前 VectorIterator 指定的項目位址。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 VectorIterator 指定的項目。

## <a name="operator-equality"></a>  Vectoriterator:: Operator = = 運算子

指出目前 VectorIterator 是否等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果目前 VectorIterator 等於 `true` 則為 `other`，否則為 `false`。

## <a name="operator-greater-than"></a>  Vectoriterator:: Operator&gt;運算子

指出目前 VectorIterator 是否大於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

`true` 如果目前 VectorIterator 大於`other`; 否則`false`。

## <a name="operator-greater-than-or-equals"></a>  Vectoriterator:: Operator&gt;= 運算子

指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果目前 VectorIterator 大於或等於 `true` 則為 `other`，否則為 `false`。

## <a name="operator-increment"></a>  Vectoriterator:: Operator + + 運算子

遞增目前 VectorIterator。

### <a name="syntax"></a>語法

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>傳回值

第一種語法會先遞增再傳回目前 VectorIterator。 第二種語法傳回目前 VectorIterator 的複本，然後遞增目前 VectorIterator。

### <a name="remarks"></a>備註

第一種 VectorIterator 語法會預先遞增目前 VectorIterator。

第二種語法會事後遞增目前 VectorIterator。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。

## <a name="operator-inequality"></a>  Vectoriterator:: Operator ！ = 運算子

指出目前 VectorIterator 是否不等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

`true` 如果目前 VectorIterator 是否不等於`other`; 否則`false`。

## <a name="operator-less-than"></a>  Vectoriterator:: Operator&lt;運算子

指出目前 VectorIterator 是否小於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果目前 VectorIterator 小於 `true` 則為 `other`，否則為 `false`。

## <a name="operator-less-than-or-equals"></a>  Vectoriterator:: Operator&lt;= 運算子

指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

`true` 如果目前 VectorIterator 是否小於或等於`other`; 否則`false`。

## <a name="operator-minus"></a>  Vectoriterator:: Operator-運算子

從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。

### <a name="syntax"></a>語法

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*n*<br/>
項目數。

*other*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

第一個運算子語法會傳回的 VectorIterator 物件`n`目前 VectorIterator 大於或等於的項目。 第二個運算子語法則傳回的項目之間目前和`other`VectorIterator。

## <a name="operator-plus-assign"></a>  Vectoriterator:: Operator + = 運算子

依指定的位移值遞增目前 VectorIterator。

### <a name="syntax"></a>語法

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>參數

*n*<br/>
整數位移。

### <a name="return-value"></a>傳回值

更新後的 VectorIterator。

## <a name="operator-plus"></a>  ectorIterator::operator + 運算子

傳回 VectorIterator ，參考從指定的 VectorIterator 開始指定位移的項目。

### <a name="syntax"></a>語法

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>參數

*T*<br/>
在第二個語法中，是 VectorIterator 的 typename。

*n*<br/>
整數位移。

*i*<br/>
在第二個語法中是 VectorIterator。

### <a name="return-value"></a>傳回值

在第一個語法中是 VectorIterator，參考從目前 VectorIterator 開始指定位移的項目。

在第二個語法中是 VectorIterator，參考從參數 `i` 的開頭開始指定位移的項目。

### <a name="remarks"></a>備註

第一個語法範例

## <a name="operator-minus-equals"></a>  Vectoriterator:: Operator-= 運算子

依指定的位移遞減目前 VectorIterator。

### <a name="syntax"></a>語法

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>參數

*n*<br/>
整數位移。

### <a name="return-value"></a>傳回值

更新後的 VectorIterator。

## <a name="operator-at"></a>  VectorIterator::operator\[\]

擷取從目前 VectorIterator 開始指定偏移的元素的參考。

### <a name="syntax"></a>語法

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>參數

*n*<br/>
整數位移。

### <a name="return-value"></a>傳回值

從目前 VectorIterator 偏移 `n` 個元素的元素。

## <a name="ctor"></a>  Vectoriterator:: Vectoriterator 建構函式

初始化 VectorIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>參數

*v*<br/>
IVector\<T > 物件。

### <a name="remarks"></a>備註

第一個語法範例是預設建構函式。 第二個語法範例是明確建構函式用來建構從 Ivector<platform VectorIterator\<T > 物件。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)