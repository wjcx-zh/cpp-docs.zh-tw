---
title: Platform::Collections::VectorViewIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 3fed25b975eefe33f9eb7014ca91a52ba419c936
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211563"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator 類別

為衍生自 Windows 執行階段介面的物件提供標準樣板程式庫反覆運算器 `IVectorView` 。

`ViewVectorIterator` 這個 Proxy 迭代器可以儲存類型為 `VectorProxy<T>`的元素。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

## <a name="syntax"></a>語法

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>參數

*T*<br/>
VectorViewIterator 樣板類別的 typename。

### <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`difference_type`|指標差異 (ptrdiff_t)。|
|`iterator_category`|隨機存取迭代器的分類 (::std::random_access_iterator_tag)。|
|`pointer`|VectorViewIterator 的實作所需的內部類型指標。|
|`reference`|VectorViewIterator 的實作所需的內部類型參考。|
|`value_type`|`T` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[VectorViewIterator：： VectorViewIterator](#ctor)|初始化 VectorViewIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[VectorViewIterator：： operator-運算子](#operator-minus)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|
|[VectorViewIterator：： operator--運算子](#operator-decrement)|遞減目前 VectorViewIterator。|
|[VectorViewIterator：： operator！ = 運算子](#operator-inequality)|指出目前 VectorViewIterator 是否不等於指定的 VectorViewIterator。|
|[VectorViewIterator：： operator * 運算子](#operator-dereference)|擷取目前 VectorViewIterator 指定的元素的參考。|
|[VectorViewIterator：： operator\[\]](#operator-at)|擷取從目前 VectorViewIterator 開始指定位移之項目的參考。|
|[VectorViewIterator：： operator + 運算子](#operator-plus)|傳回 VectorViewIterator ，參考從指定的 VectorViewIterator 開始指定位移的項目。|
|[VectorViewIterator：： operator + + 運算子](#operator-increment)|遞增目前 VectorViewIterator。|
|[VectorViewIterator：： operator + = 運算子](#operator-plus-equals)|依指定的位移遞增目前 VectorViewIterator。|
|[VectorViewIterator：： operator< 運算子](#operator-less-than)|指出目前 VectorViewIterator 是否小於指定的 VectorViewIterator。|
|[VectorViewIterator：： operator \< = 運算子](#operator-less-than-or-equals)|指出目前 VectorViewIterator 是否小於或等於指定的 VectorViewIterator。|
|[VectorViewIterator：： operator-= 運算子](#operator-minus-assign)|依指定的位移值遞減目前 VectorViewIterator。|
|[VectorViewIterator：： operator = = 運算子](#operator-equality)|指出目前 VectorViewIterator 是否等於指定的 VectorViewIterator。|
|[VectorViewIterator::operator> 運算子](#operator-greater-than)|指出目前 VectorViewIterator 是否大於指定的 VectorViewIterator。|
|[VectorViewIterator：： operator-> 運算子](#operator-arrow)|擷取目前 VectorViewIterator 參考的元素的位址。|
|[VectorViewIterator：： operator>= 運算子](#operator-greater-than-or-equals)|指出目前 VectorViewIterator 是否大於或等於指定的 VectorViewIterator。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VectorViewIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorViewIterator：： operator- &gt; 運算子

擷取目前 VectorViewIterator 參考的元素的位址。

### <a name="syntax"></a>語法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>傳回值

目前 VectorViewIterator 參考的項目值。

傳回值的類型是實作這個運算子所需之未指定的內部類型。

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator：： operator--運算子

遞減目前 VectorViewIterator。

### <a name="syntax"></a>語法

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>傳回值

第一種語法會先遞減再傳回目前 VectorViewIterator。 第二種語法會傳回目前 VectorViewIterator 的複本，然後遞減目前 VectorViewIterator。

### <a name="remarks"></a>備註

第一種 VectorViewIterator 語法會前置遞減目前 VectorViewIterator。

第二種語法會後置遞減目前 VectorViewIterator。 **`int`** 第二個語法中的類型表示遞減後作業，而不是實際的整數運算元。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>VectorViewIterator：： operator \* 運算子

擷取目前 VectorViewIterator 指定的元素的參考。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 VectorViewIterator 指定的項目。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator：： operator = = 運算子

指出目前 VectorViewIterator 是否等於指定的 VectorViewIterator。

### <a name="syntax"></a>語法

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 `VectorViewIterator` 等於*其他*，則為，否則為 **`false`** 。

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorViewIterator：： operator &gt; 運算子

指出目前 VectorViewIterator 是否大於指定的 VectorViewIterator。

### <a name="syntax"></a>語法

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 VectorViewIterator 大於*其他*，則為，否則為 **`false`** 。

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator：： operator &gt; = 運算子

指出目前的是否 `VectorViewIterator` 大於或等於指定的 `VectorViewIterator` 。

### <a name="syntax"></a>語法

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 `VectorViewIterator` 大於或等於*其他*，則為，否則為 **`false`** 。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>VectorViewIterator：： operator + + 運算子

遞增目前 VectorViewIterator。

### <a name="syntax"></a>語法

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>傳回值

第一種語法會先遞增再傳回目前 VectorViewIterator。 第二種語法會傳回目前 VectorViewIterator 的複本，然後遞增目前 VectorViewIterator。

### <a name="remarks"></a>備註

第一種 VectorViewIterator 語法會前置遞增目前 VectorViewIterator。

第二種語法會後置遞增目前 VectorViewIterator。 **`int`** 第二個語法中的類型表示遞增後作業，而不是實際的整數運算元。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>VectorViewIterator：： operator！ = 運算子

指出目前 VectorViewIterator 是否不等於指定的 VectorViewIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的不 `VectorViewIterator` 等於*其他*，則為，否則為 **`false`** 。

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorViewIterator：： operator &lt; 運算子

指出目前 VectorIterator 是否小於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 `VectorIterator`。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 `VectorIterator` 小於*其他*，則為，否則為 **`false`** 。

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator：： operator &lt; = 運算子

指出目前的是否 `VectorIterator` 小於或等於指定的 `VectorIterator` 。

### <a name="syntax"></a>語法

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 `VectorIterator`。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 `VectorIterator` 小於或等於*其他*，則為，否則為 **`false`** 。

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>VectorViewIterator：： operator-運算子

從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。

### <a name="syntax"></a>語法

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*n*<br/>
項目數。

*另一方面*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

第一個運算子語法會傳回比目前 VectorViewIterator 少 `n` 個項目的 VectorViewIterator 物件。 第二個運算子語法則傳回目前和 `other` VectorViewIterator 之間的項目數。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>VectorViewIterator：： operator + = 運算子

依指定的位移遞增目前 VectorViewIterator。

### <a name="syntax"></a>語法

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>參數

*n*<br/>
整數位移。

### <a name="return-value"></a>傳回值

更新後的 VectorViewIterator。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator：： operator + 運算子

傳回 VectorViewIterator ，參考從指定的 VectorViewIterator 開始指定位移的項目。

### <a name="syntax"></a>語法

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>參數

*T*<br/>
在第二個語法中，是 VectorViewIterator 的 typename。

*n*<br/>
整數位移。

*i*<br/>
在第二個語法中是 VectorViewIterator。

### <a name="return-value"></a>傳回值

在第一個語法中是 VectorViewIterator，參考從目前 VectorViewIterator 開始指定位移的項目。

在第二個語法中是 VectorViewIterator，參考從參數 `i` 的開頭開始指定位移的項目。

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>VectorViewIterator：： operator-= 運算子

依指定的位移遞減目前 VectorIterator。

### <a name="syntax"></a>語法

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>參數

*n*<br/>
整數位移。

### <a name="return-value"></a>傳回值

更新後的 VectorIterator。

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator：： operator\[\]

擷取從目前 VectorViewIterator 開始指定位移之項目的參考。

### <a name="syntax"></a>語法

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>參數

*n*<br/>
整數位移。

### <a name="return-value"></a>傳回值

從目前 VectorViewIterator 位移 `n` 個項目的項目。

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator：： VectorViewIterator 函式

初始化 VectorViewIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>參數

*&*<br/>
IVectorView \<T> 物件。

### <a name="remarks"></a>備註

第一個語法範例是預設建構函式。 第二個語法範例是明確的函式，用來從 IVectorView 物件中建立 VectorViewIterator \<T> 。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
