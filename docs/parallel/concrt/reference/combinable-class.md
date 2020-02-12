---
title: combinable 類別
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: a1954cd3a69233deed053da5b5fdef0dbc183b80
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141437"
---
# <a name="combinable-class"></a>combinable 類別

`combinable<T>` 物件適用於提供資料的執行緒私用複本，在平行演算法期間執行無鎖定的執行緒-本機子運算。 在平行作業結尾處，可以將執行緒私用子運算合併於最終結果。 這個類別可以用來代替共用變數，而且如果該共用變數有許多爭用情形，則可能可以改進效能。

## <a name="syntax"></a>語法

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>參數

*T*<br/>
最後合併結果的資料類型。 型別必須有複製的「函式」和「預設」的「函數」。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[combinable](#ctor)|已多載。 建構新的 `combinable` 物件。|
|[~ 組合的析構函式](#dtor)|終結 `combinable` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[清除](#clear)|清除先前使用方式的任何中繼計算結果。|
|[combine](#combine)|藉由呼叫所提供的結合仿函數，從執行緒區域子計算的集合中計算出最後的值。|
|[combine_each](#combine_each)|藉由呼叫每個執行緒區域子計算一次所提供的結合仿函數，計算執行緒區域子計算集合中的最後一個值。 最後的結果是由函式物件累積。|
|[local](#local)|已多載。 傳回執行緒私用子計算的參考。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|將另一個 `combinable` 物件的指派給 `combinable` 物件。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`combinable`

## <a name="requirements"></a>需求

**標頭：** ppl。h

**命名空間：** concurrency

## <a name="clear"></a>明確

清除先前使用方式的任何中繼計算結果。

```cpp
void clear();
```

## <a name="ctor"></a>combinable

建構新的 `combinable` 物件。

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>參數

*_Function*<br/>
初始化仿函數物件的類型。

*_FnInitialize*<br/>
將呼叫的函式，以初始化 `T`類型的每個新的執行緒私用值。 它必須支援具有簽章 `T ()`的函式呼叫運算子。

*_Copy*<br/>
要複製到其中的現有 `combinable` 物件。

### <a name="remarks"></a>備註

第一個函式會使用 `T`類型的預設的函式，初始化新的元素。

第二個函式會使用提供做為 `_FnInitialize` 參數的初始化仿函數，初始化新的專案。

第三個函式是複製的「函數」。

## <a name="dtor"></a>~ 組合

終結 `combinable` 物件。

```cpp
~combinable();
```

## <a name="combine"></a>起來

藉由呼叫所提供的結合仿函數，從執行緒區域子計算的集合中計算出最後的值。

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>參數

*_Function*<br/>
函式物件的型別，將叫用此類型來結合兩個執行緒區域子計算。

*_FnCombine*<br/>
用來結合子計算的仿函數。 其簽章為 `T (T, T)` 或 `T (const T&, const T&)`，而且必須是關聯和交換。

### <a name="return-value"></a>傳回值

結合所有線程-私用子計算的最終結果。

## <a name="combine_each"></a>combine_each

藉由呼叫每個執行緒區域子計算一次所提供的結合仿函數，計算執行緒區域子計算集合中的最後一個值。 最後的結果是由函式物件累積。

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>參數

*_Function*<br/>
函式物件的型別，將叫用此類型來結合單一線程區域子計算。

*_FnCombine*<br/>
用來結合一個子計算的仿函數。 其簽章為 `void (T)` 或 `void (const T&)`，而且必須是關聯和交換。

## <a name="local"></a>本機

傳回執行緒私用子計算的參考。

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>參數

*_Exists*<br/>
布林值的參考。 這個引數所參考的布林值將會設定為**true** 。如果子運算已經存在於這個執行緒上，並且設定為**false** （如果這是此執行緒的第一個子計算）。

### <a name="return-value"></a>傳回值

執行緒私用子計算的參考。

## <a name="operator_eq"></a>operator =

將另一個 `combinable` 物件的指派給 `combinable` 物件。

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>參數

*_Copy*<br/>
要複製到其中的現有 `combinable` 物件。

### <a name="return-value"></a>傳回值

這個 `combinable` 物件的參考。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
