---
title: Platform::Collections::VectorIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: e649027c2ba3f637c42765af691f4d321913fb28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354373"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator 類別

為從 Windows 運行時 IVector 介面派生的物件提供標準範本庫反覆運算器。

向量反覆運算體是存儲向量代理\<T>类型的元素的代理迭代器。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

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
|`pointer`|指向內部類型的指標,Platform::集合::D尾::VectorProxy\<T>,這是實現 VectorItatateror 所必需的。|
|`reference`|對內部類型的引用,Platform::集合::D尾::VectorProxy\<T>,這是實現 VectorItatererererererererererererererererererererere rerererererererererererererererererererererererererererererererererererererererererererererererererererererer.|
|`value_type`|`T` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[向量反覆發代器:向量反覆運算器](#ctor)|初始化 VectorIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[向量反覆運算器::運算符-運算子](#operator-minus)|從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。|
|[向量反覆運算器::運算元 -- 運算子](#operator-decrement)|遞減目前 VectorIterator。|
|[向量反覆運算器::運算元!= 運算子](#operator-inequality)|指出目前 VectorIterator 是否不等於指定的 VectorIterator。|
|[向量反覆運算器::運算符* 運算子](#operator-dereference)|擷取目前 VectorIterator 指定之元素的參考。|
|[向量反覆運算器::運算子\[\]](#operator-at)|擷取從目前 VectorIterator 開始指定偏移的元素的參考。|
|[向量反覆運算器::運算符+ 運算子](#operator-plus)|傳回 VectorIterator ，參考從指定的 VectorIterator 開始指定位移的項目。|
|[向量反覆運算器::運算符* 運算子](#operator-increment)|遞增目前 VectorIterator。|
|[向量反覆運算器::運算符= 運算子](#operator-plus-assign)|依指定的位移值遞增目前 VectorIterator。|
|[向量反覆運算器::運算符<運算符](#operator-less-than)|指出目前 VectorIterator 是否小於指定的 VectorIterator。|
|[向量反覆運算器::運算符\<= 運算子](#operator-less-than-or-equals)|指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。|
|[向量反覆運算器::運算符-= 運算子](#operator-minus-equals)|依指定的位移遞減目前 VectorIterator。|
|[向量反覆運算器::運算符 = 運算子](#operator-equality)|指出目前 VectorIterator 是否等於指定的 VectorIterator。|
|[VectorIterator::operator> 運算子](#operator-greater-than)|指出目前 VectorIterator 是否大於指定的 VectorIterator。|
|[向量反覆運算器::運算符->运算符](#operator-arrow)|擷取目前 VectorIterator 參考的元素的位址。|
|[向量反覆運算器::運算符>= 運算子](#operator-greater-than-or-equals)|指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`VectorIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>向量反覆發者::運算子-&gt;運算子

擷取目前 VectorIterator 參考的元素的位址。

### <a name="syntax"></a>語法

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>傳回值

目前 VectorIterator 參考的項目值。

傳回值的類型是實作這個運算子所需之未指定的內部類型。

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>向量反覆運算器::運算元 -- 運算子

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

第二種語法會後置遞減目前的 VectorIterator。 第二種語法中的 `int` 類型表示後置遞減作業，不是實際的整數運算元。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>向量反覆運算器::運算子\*

擷取目前 VectorIterator 指定的項目位址。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 VectorIterator 指定的項目。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>向量反覆運算器::運算符 = 運算子

指出目前 VectorIterator 是否等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果目前向量反覆發代器等於*其他*,**則為 true** 。否則,**假**。

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>向量反覆運算器::運算子&gt;

指出目前 VectorIterator 是否大於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果目前向量反覆運算器大於*其他*,**則為 true** ;否則,**假**。

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>向量反覆運算器::運算符&gt;= 運算子

指出目前 VectorIterator 是否大於或等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果當前向量反覆運算器大於或等於*其他*,**則為 true;** 否則,**假**。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>向量反覆運算器::運算符* 運算子

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>向量反覆運算器::運算元!= 運算子

指出目前 VectorIterator 是否不等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果當前向量反覆運算器不等於*其他*,**則為 true;** 否則,**假**。

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>向量反覆運算器::運算子&lt;

指出目前 VectorIterator 是否小於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

**如果**目前向量反覆運算器小於*其他*, 為 true ;否則,**假**。

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>向量反覆運算器::運算符&lt;= 運算子

指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。

### <a name="syntax"></a>語法

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

如果當前向量反覆運算器小於或等於*其他*,**則為 true;** 否則,**假**。

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>向量反覆運算器::運算符-運算子

從目前迭代器減去指定的項目數而產生新的迭代器，或從目前迭代器減去指定的迭代器而產生迭代器之間的項目數。

### <a name="syntax"></a>語法

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>參數

*n*<br/>
項目數。

*其他*<br/>
另一個 VectorIterator。

### <a name="return-value"></a>傳回值

第一個運算子語法會傳回比目前 VectorIterator 少 `n` 個項目的 VectorIterator 物件。 第二個運算子語法則傳回目前和 `other` VectorIterator 之間的項目數。

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>向量反覆運算器::運算符= 運算子

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

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>向量反覆運算器::運算符+ 運算子

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

*I.*<br/>
在第二個語法中是 VectorIterator。

### <a name="return-value"></a>傳回值

在第一個語法中是 VectorIterator，參考從目前 VectorIterator 開始指定位移的項目。

在第二個語法中是 VectorIterator，參考從參數 `i` 的開頭開始指定位移的項目。

### <a name="remarks"></a>備註

第一個語法範例

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>向量反覆運算器::運算符-= 運算子

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

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>向量反覆運算器::運算子\[\]

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

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>向量反覆運算器:向量反覆運算器建構函數

初始化 VectorIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>參數

*五*<br/>
IVector\<T>物件。

### <a name="remarks"></a>備註

第一個語法範例是預設建構函式。 第二個語法示例是顯式構造函數,用於從IVector\<T>对象构造VectorIteror。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)
