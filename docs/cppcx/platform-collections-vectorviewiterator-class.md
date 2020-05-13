---
title: Platform::Collections::VectorViewIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363702"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator 類別

為從 Windows`IVectorView`執行時 介面派生的物件提供標準範本庫反覆運算器。

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

|名稱|描述|
|----------|-----------------|
|`difference_type`|指標差異 (ptrdiff_t)。|
|`iterator_category`|隨機存取迭代器的分類 (::std::random_access_iterator_tag)。|
|`pointer`|VectorViewIterator 的實作所需的內部類型指標。|
|`reference`|VectorViewIterator 的實作所需的內部類型參考。|
|`value_type`|`T` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[向量檢視反覆發代器::向量檢視反覆運算器](#ctor)|初始化 VectorViewIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[向量檢視反覆發代器::運算元 - 運算子](#operator-minus)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|
|[向量檢視反覆發代器::運算元 -- 運算子](#operator-decrement)|遞減目前 VectorViewIterator。|
|[向量檢視反覆運算器::運算元!= 運算子](#operator-inequality)|指出目前 VectorViewIterator 是否不等於指定的 VectorViewIterator。|
|[向量檢視反覆發代器::運算符* 運算子](#operator-dereference)|擷取目前 VectorViewIterator 指定的元素的參考。|
|[向量檢視反覆發代器::運算子\[\]](#operator-at)|擷取從目前 VectorViewIterator 開始指定位移之項目的參考。|
|[向量檢視反覆發代器::運算元+ 運算子](#operator-plus)|傳回 VectorViewIterator ，參考從指定的 VectorViewIterator 開始指定位移的項目。|
|[向量檢視反覆發代器::運算符* 運算子](#operator-increment)|遞增目前 VectorViewIterator。|
|[向量檢視反覆發代器::運算符= 運算子](#operator-plus-equals)|依指定的位移遞增目前 VectorViewIterator。|
|[向量檢視反覆發代器::運算元<運算符](#operator-less-than)|指出目前 VectorViewIterator 是否小於指定的 VectorViewIterator。|
|[向量檢視反覆發代器::運算符\<= 運算子](#operator-less-than-or-equals)|指出目前 VectorViewIterator 是否小於或等於指定的 VectorViewIterator。|
|[向量檢視反覆發代器::運算符-= 運算子](#operator-minus-assign)|依指定的位移值遞減目前 VectorViewIterator。|
|[向量檢視反覆發代器::運算符 = 運算子](#operator-equality)|指出目前 VectorViewIterator 是否等於指定的 VectorViewIterator。|
|[VectorViewIterator::operator> 運算子](#operator-greater-than)|指出目前 VectorViewIterator 是否大於指定的 VectorViewIterator。|
|[向量檢視反覆運算器::運算符->运算符](#operator-arrow)|擷取目前 VectorViewIterator 參考的元素的位址。|
|[向量檢視反覆發代器::運算元>= 運算子](#operator-greater-than-or-equals)|指出目前 VectorViewIterator 是否大於或等於指定的 VectorViewIterator。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VectorViewIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>向量檢視反覆發代器::運算元 -&gt;運算子

擷取目前 VectorViewIterator 參考的元素的位址。

### <a name="syntax"></a>語法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>傳回值

目前 VectorViewIterator 參考的項目值。

傳回值的類型是實作這個運算子所需之未指定的內部類型。

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>向量檢視反覆發代器::運算元 -- 運算子

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

第二種語法會後置遞減目前 VectorViewIterator。 第二種語法中的 `int` 類型表示後置遞減作業，不是實際的整數運算元。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>向量檢視反覆發代器::運算元\*運算子

擷取目前 VectorViewIterator 指定的元素的參考。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 VectorViewIterator 指定的項目。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>向量檢視反覆發代器::運算符 = 運算子

指出目前 VectorViewIterator 是否等於指定的 VectorViewIterator。

### <a name="syntax"></a>語法

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

**如果**電`VectorViewIterator`流 等於*其他*, 則為 true ;否則,**假**。

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>向量檢視反覆發代器::運算元&gt;運算子

指出目前 VectorViewIterator 是否大於指定的 VectorViewIterator。

### <a name="syntax"></a>語法

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

如果目前向量檢視器大於*其他*,**則為 true** ;否則,**假**。

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>向量檢視反覆發代器::運算符&gt;= 運算子

指示電流`VectorViewIterator`是否大於或等於指定`VectorViewIterator`的 。

### <a name="syntax"></a>語法

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

**如果**電`VectorViewIterator`流 大於或等於*其他*;否則,**假**。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>向量檢視反覆發代器::運算符* 運算子

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

第二種語法會後置遞增目前 VectorViewIterator。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>向量檢視反覆運算器::運算元!= 運算子

指出目前 VectorViewIterator 是否不等於指定的 VectorViewIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

如果電流`VectorViewIterator`不等於*其他*,**則為 true;** 否則,**假**。

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>向量檢視反覆發代器::運算元&lt;運算子

指出目前 VectorIterator 是否小於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 `VectorIterator`。

### <a name="return-value"></a>傳回值

**如果**電`VectorIterator`流 小於*其他*, 則為 true ;否則,**假**。

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>向量檢視反覆發代器::運算符&lt;= 運算子

指示電流`VectorIterator`是否小於或等於指定`VectorIterator`的 。

### <a name="syntax"></a>語法

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 `VectorIterator`。

### <a name="return-value"></a>傳回值

**如果**電`VectorIterator`流 小於或等於*其他*;否則,**假**。

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>向量檢視反覆發代器::運算元 - 運算子

從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。

### <a name="syntax"></a>語法

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>參數

*n*<br/>
項目數。

*其他*<br/>
另一個 VectorViewIterator。

### <a name="return-value"></a>傳回值

第一個運算子語法會傳回比目前 VectorViewIterator 少 `n` 個項目的 VectorViewIterator 物件。 第二個運算子語法則傳回目前和 `other` VectorViewIterator 之間的項目數。

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>向量檢視反覆發代器::運算符= 運算子

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

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>向量檢視反覆發代器::運算元+ 運算子

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

*I.*<br/>
在第二個語法中是 VectorViewIterator。

### <a name="return-value"></a>傳回值

在第一個語法中是 VectorViewIterator，參考從目前 VectorViewIterator 開始指定位移的項目。

在第二個語法中是 VectorViewIterator，參考從參數 `i` 的開頭開始指定位移的項目。

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>向量檢視反覆發代器::運算符-= 運算子

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

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>向量檢視反覆發代器::運算子\[\]

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

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>向量檢視反覆運算器::向量檢視反覆運算器建構函數

初始化 VectorViewIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>參數

*五*<br/>
iVectorView\<T>物件。

### <a name="remarks"></a>備註

第一個語法範例是預設建構函式。 第二個語法示例是顯式構造函數,用於從IVectorView\<T>对象构造VectorViewIteror。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)
