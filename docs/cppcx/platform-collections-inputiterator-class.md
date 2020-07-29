---
title: Platform::Collections::InputIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 4aeef07a34c04bd1ab47acf808026024faada567
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218425"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator 類別

為衍生自 Windows 執行階段的集合提供標準範本程式庫 InputIterator。

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

|名稱|說明|
|----------|-----------------|
|`difference_type`|指標差異 (ptrdiff_t)。|
|`iterator_category`|輸入迭代器的類別 (::std::input_iterator_tag)。|
|`pointer`|指向的指標`const X`|
|`reference`|`const X` 的參考|
|`value_type`|`X` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[InputIterator：： InputIterator](#ctor)|初始化 InputIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[InputIterator：： operator！ = 運算子](#operator-inequality)|指出目前 InputIterator 是否不等於指定的 InputIterator。|
|[InputIterator::operator* 運算子](#operator-dereference)|擷取目前 InputIterator 指定之項目的參考。|
|[InputIterator：： operator + + 運算子](#operator-increment)|遞增目前 InputIterator。|
|[InputIterator：： operator = = 運算子](#operator-equality)|指出目前 InputIterator 是否等於指定的 InputIterator。|
|[InputIterator：： operator-> 運算子](#operator-arrow)|擷取目前 InputIterator 參考的項目位址。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`InputIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator：： InputIterator 函式

初始化 InputIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>參數

*定位*<br/>
迭代器物件。

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator：： operator- &gt; 運算子

擷取目前 InputIterator 指定的項目位址。

### <a name="syntax"></a>語法

```
pointer operator->() const;
```

### <a name="return-value"></a>傳回值

目前 InputIterator 指定的項目位址。

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator：： operator \* 運算子

擷取目前 InputIterator 指定之項目的參考。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 InputIterator 指定的項目。

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator：： operator = = 運算子

指出目前 InputIterator 是否等於指定的 InputIterator。

### <a name="syntax"></a>語法

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 InputIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 InputIterator 等於*其他*，則為，否則為 **`false`** 。

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator：： operator + + 運算子

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

第二種語法會後置遞增目前 InputIterator。 **`int`** 第二個語法中的類型表示遞增後作業，而不是實際的整數運算元。

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator：： operator！ = 運算子

指出目前 InputIterator 是否不等於指定的 InputIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個 InputIterator。

### <a name="return-value"></a>傳回值

**`true`** 如果目前的 InputIterator 不等於*其他*，則為，否則為 **`false`** 。

## <a name="see-also"></a>另請參閱

[Platform 命名空間](platform-namespace-c-cx.md)
