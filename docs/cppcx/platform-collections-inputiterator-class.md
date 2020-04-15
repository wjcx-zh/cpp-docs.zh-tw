---
title: Platform::Collections::InputIterator 類別
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354557"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator 類別

為從 Windows 運行時派生的集合提供標準範本庫輸入反覆運算器。

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
|`pointer`|指向的指標`const X`|
|`reference`|`const X` 的參考|
|`value_type`|`X` typename。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[輸入反覆運算器::輸入式發運算器](#ctor)|初始化 InputIterator 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[輸入反覆運算器::操作員!= 操作員](#operator-inequality)|指出目前 InputIterator 是否不等於指定的 InputIterator。|
|[InputIterator::operator* 運算子](#operator-dereference)|擷取目前 InputIterator 指定之項目的參考。|
|[輸入反覆運算器::運算子* 運算子](#operator-increment)|遞增目前 InputIterator。|
|[輸入反覆運算器::運算符 = 運算子](#operator-equality)|指出目前 InputIterator 是否等於指定的 InputIterator。|
|[輸入反覆運算器::操作員->运算符](#operator-arrow)|擷取目前 InputIterator 參考的項目位址。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`InputIterator`

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>輸入反覆運算器::輸入反覆運算器建構函數

初始化 InputIterator 類別的新執行個體。

### <a name="syntax"></a>語法

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>參數

*反覆運算*<br/>
迭代器物件。

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>輸入迭代器::管理員-&gt;管理員

擷取目前 InputIterator 指定的項目位址。

### <a name="syntax"></a>語法

```
pointer operator->() const;
```

### <a name="return-value"></a>傳回值

目前 InputIterator 指定的項目位址。

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>輸入反覆運算器::操作員\*

擷取目前 InputIterator 指定之項目的參考。

### <a name="syntax"></a>語法

```
reference operator*() const;
```

### <a name="return-value"></a>傳回值

目前 InputIterator 指定的項目。

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>輸入反覆運算器::運算符 = 運算子

指出目前 InputIterator 是否等於指定的 InputIterator。

### <a name="syntax"></a>語法

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 InputIterator。

### <a name="return-value"></a>傳回值

如果目前輸入反覆運算器等於*其他*輸入反覆運算器,**則為 true;** 否則,**假**。

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>輸入反覆運算器::運算子* 運算子

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

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>輸入反覆運算器::操作員!= 操作員

指出目前 InputIterator 是否不等於指定的 InputIterator。

### <a name="syntax"></a>語法

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>參數

*其他*<br/>
另一個 InputIterator。

### <a name="return-value"></a>傳回值

如果目前輸入反覆運算器不等於*其他*輸入反覆運算器,**則為 true;** 否則,**假**。

## <a name="see-also"></a>另請參閱

[平台命名空間](platform-namespace-c-cx.md)
