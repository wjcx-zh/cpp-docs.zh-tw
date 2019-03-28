---
title: Platform::Collections::InputIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 49b131b01fe3d9cad5f8366fd4cc0c110b5d060c
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565135"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator 類別

衍生自 Windows 執行階段的集合提供標準樣板程式庫 InputIterator。

## <a name="syntax"></a>語法

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>參數

*X*<br/>
InputIterator 樣板類別的 typename。

### <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`difference_type`|指標差異 (ptrdiff_t)。|
|`iterator_category`|輸入迭代器的類別 (::std::input_iterator_tag)。|
|`pointer`|指標 `const X`|
|`reference`|參考 `const X`|
|`value_type`|`X` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|初始化 InputIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[InputIterator::operator!= 運算子](#operator-inequality)|指出目前 InputIterator 是否不等於指定的 InputIterator。|
|[InputIterator::operator* 運算子](#operator-dereference)|擷取目前 InputIterator 指定之項目的參考。|
|[InputIterator::operator++ 運算子](#operator-increment)|遞增目前 InputIterator。|
|[InputIterator::operator== 運算子](#operator-equality)|指出目前 InputIterator 是否等於指定的 InputIterator。|
|[InputIterator::operator-> 運算子](#operator-arrow)|擷取目前 InputIterator 參考的項目位址。|

## <a name="inheritance-hierarchy"></a>繼承階層

`InputIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="ctor"></a>  Inputiterator:: Inputiterator 建構函式

初始化 InputIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>參數

*iterator*<br/>
迭代器物件。

## <a name="operator-arrow"></a>  Inputiterator:: Operator-&gt;運算子

擷取目前 InputIterator 指定的項目位址。

### <a name="syntax"></a>語法

```
pointer operator->() const;
```

### <a name="return-value"></a>傳回值

目前 InputIterator 指定的項目位址。

## <a name="operator-dereference"></a>  Inputiterator:: Operator\*運算子

擷取目前 InputIterator 指定之項目的參考。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 InputIterator 指定的項目。

## <a name="operator-equality"></a>  Inputiterator:: Operator = = 運算子

指出目前 InputIterator 是否等於指定的 InputIterator。

### <a name="syntax"></a>語法

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 InputIterator。

### <a name="return-value"></a>傳回值

**true**是否等於目前 InputIterator*其他*; 否則**false**。

## <a name="operator-increment"></a>  Inputiterator:: Operator + + 運算子

遞增目前 InputIterator。

### <a name="syntax"></a>語法

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>傳回值

第一種語法會先遞增再傳回目前 InputIterator。 第二種語法會傳回目前 InputIterator 的複本，然後遞增目前 InputIterator。

### <a name="remarks"></a>備註

第一種 InputIterator 語法會前置遞增目前 InputIterator。

第二種語法會後置遞增目前 InputIterator。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。

## <a name="operator-inequality"></a>  Inputiterator:: Operator ！ = 運算子

指出目前 InputIterator 是否不等於指定的 InputIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>參數

*other*<br/>
另一個 InputIterator。

### <a name="return-value"></a>傳回值

**真**目前 InputIterator 是否不等於*其他*; 否則**false**。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
