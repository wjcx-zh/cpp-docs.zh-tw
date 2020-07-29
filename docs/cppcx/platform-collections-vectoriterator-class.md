---
title: Platform::Collections::VectorIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: bade67a104774c3ab6187e250c6faf6969002c0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218412"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator 類別

為衍生自 Windows 執行階段 IVector 介面的物件提供標準樣板程式庫反覆運算器。

VectorIterator 是一個 proxy 反覆運算器，它會儲存 VectorProxy 類型的元素 \<T> 。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

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

|名稱|說明|
|----------|-----------------|
|`difference_type`|指標差異 (ptrdiff_t)。|
|`iterator_category`|隨機存取迭代器的分類 (::std::random_access_iterator_tag)。|
|`pointer`|VectorIterator 執行所需之內部類型 Platform：： collection：:D etails：： VectorProxy 的指標 \<T> 。|
|`reference`|VectorIterator 執行所需之內部類型 Platform：： collection：:D etails：： VectorProxy 的參考 \<T> 。|
|`value_type`|`T` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[VectorIterator：： VectorIterator](#ctor)|初始化 VectorIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[VectorIterator：： operator-運算子](#operator-minus)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|
|[VectorIterator：： operator--運算子](#operator-decrement)|遞減目前 VectorIterator。|
|[VectorIterator：： operator！ = 運算子](#operator-inequality)|指出目前 VectorIterator 是否不等於指定的 VectorIterator。|
|[VectorIterator：： operator * 運算子](#operator-dereference)|擷取目前 VectorIterator 指定之元素的參考。|
|[VectorIterator：： operator\[\]](#operator-at)|擷取從目前 VectorIterator 開始指定偏移的元素的參考。|
|[VectorIterator：： operator + 運算子](#operator-plus)|傳回 VectorIterator ，參考從指定的 VectorIterator 開始指定位移的項目。|
|[VectorIterator：： operator + + 運算子](#operator-increment)|遞增目前 VectorIterator。|
|[VectorIterator：： operator + = 運算子](#operator-plus-assign)|依指定的位移值遞增目前 VectorIterator。|
|[VectorIterator：： operator< 運算子](#operator-less-than)|指出目前 VectorIterator 是否小於指定的 VectorIterator。|
|[VectorIterator：： operator \< = 運算子](#operator-less-than-or-equals)|指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。|
|[VectorIterator：： operator-= 運算子](#operator-minus-equals)|依指定的位移遞減目前 VectorIterator。|
|[VectorIterator：： operator = = 運算子](#operator-equality)|指出目前 VectorIterator 是否等於指定的 VectorIterator。|
|[VectorIterator::operator> 運算子](#operator-greater-than)|指出目前 VectorIterator 是否大於指定的 VectorIterator。|
|[VectorIterator：： operator-> 運算子](#operator-arrow)|擷取目前 VectorIterator 參考的元素的位址。|
|[VectorIterator：： operator>= 運算子](#operator-greater-than-or-equals)|指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VectorIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorIterator：： operator- &gt; 運算子

擷取目前 VectorIterator 參考的元素的位址。

### <a name="syntax"></a>語法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>傳回值

目前 VectorIterator 參考的項目值。

傳回值的類型是實作這個運算子所需之未指定的內部類型。

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>VectorIterator：： operator--運算子

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

第二種語法會後置遞減目前的 VectorIterator。 **`int`** 第二個語法中的類型表示遞減後作業，而不是實際的整數運算元。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>VectorIterator：： operator \* 運算子

擷取目前 VectorIterator 指定的項目位址。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 VectorIterator 指定的項目。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>VectorIterator：： operator = = 運算子

指出目前 VectorIterator 是否等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorIterator 等於*其他*，則為，否則為 **`false`** 。

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorIterator：： operator &gt; 運算子

指出目前 VectorIterator 是否大於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorIterator 大於*其他*，則為，否則為 **`false`** 。

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator：： operator &gt; = 運算子

指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorIterator 大於或等於*其他*，則為，否則為 **`false`** 。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>VectorIterator：： operator + + 運算子

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

第二種語法會事後遞增目前 VectorIterator。 **`int`** 第二個語法中的類型表示遞增後作業，而不是實際的整數運算元。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>VectorIterator：： operator！ = 運算子

指出目前 VectorIterator 是否不等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorIterator 不等於*其他*，則為，否則為 **`false`** 。

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorIterator：： operator &lt; 運算子

指出目前 VectorIterator 是否小於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorIterator 小於*其他*，則為，否則為 **`false`** 。

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator：： operator &lt; = 運算子

指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorIterator 小於或等於*其他*，則為，否則為 **`false`** 。

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>VectorIterator：： operator-運算子

從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。

### <a name="syntax"></a>語法

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*n*<br/>
項目數。

*另一方面*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

第一個運算子語法會傳回比目前 VectorIterator 少 `n` 個項目的 VectorIterator 物件。 第二個運算子語法則傳回目前和 `other` VectorIterator 之間的項目數。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>VectorIterator：： operator + = 運算子

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>VectorIterator：： operator + 運算子

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

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>VectorIterator：： operator-= 運算子

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

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>VectorIterator：： operator\[\]

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

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>VectorIterator：： VectorIterator 函式

初始化 VectorIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>參數

*&*<br/>
IVector \<T> 物件。

### <a name="remarks"></a>備註

第一個語法範例是預設建構函式。 第二個語法範例是明確的函式，用來從 IVector 物件中建立 VectorIterator \<T> 。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
