---
title: combinable 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d544ac392e2eb227d7e1c37412110d09272f10d5
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162501"
---
# <a name="combinable-class"></a>combinable 類別

`combinable<T>` 物件適用於提供資料的執行緒私用複本，在平行演算法期間執行無鎖定的執行緒-本機子運算。 在平行作業結尾處，可以將執行緒私用子運算合併於最終結果。 這個類別可以用來代替共用變數，而且如果該共用變數有許多爭用情形，則可能可以改進效能。

## <a name="syntax"></a>語法

```
template<typename T>
class combinable;
```

#### <a name="parameters"></a>參數

*T*<br/>
最後的合併結果的資料型別。 類型必須有複製建構函式和預設建構函式。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[可組合的類別](#ctor)|多載。 建構新`combinable`物件。|
|[~ combinable 解構函式](#dtor)|終結 `combinable` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[clear](#clear)|清除任何計算的中繼結果，從先前的使用方式。|
|[combine](#combine)|藉由呼叫提供的結合仿函式會計算最終的值從執行緒-本機子運算的集合。|
|[combine_each](#combine_each)|藉由呼叫執行緒區域子計算每一次提供的結合仿函式會計算最終的值從執行緒-本機子運算的集合。 最後的結果會累積函式物件。|
|[local](#local)|多載。 傳回執行緒私用子運算的參考。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|將指派給`combinable`物件從另一個`combinable`物件。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`combinable`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="clear"></a> 清除

清除任何計算的中繼結果，從先前的使用方式。

```
void clear();
```

##  <a name="ctor"></a> 可組合的類別

建構新`combinable`物件。

```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>參數

*_Function*<br/>
初始化仿函式物件的型別。

*_FnInitialize*<br/>
將呼叫來初始化類型的每個新執行緒私用值的函式`T`。 它必須支援具有簽章的函式呼叫運算子`T ()`。

*（_c)*<br/>
將現有`combinable`要複製到這個物件。

### <a name="remarks"></a>備註

第一個建構函式會初始化新的項目類型的預設建構函式`T`。

第二個建構函式會初始化新的項目使用的初始化函式，以提供`_FnInitialize`參數。

第三個建構函式是複製建構函式。

##  <a name="dtor"></a> ~ combinable

終結 `combinable` 物件。

```
~combinable();
```

##  <a name="combine"></a> 結合

藉由呼叫提供的結合仿函式會計算最終的值從執行緒-本機子運算的集合。

```
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>參數

*_Function*<br/>
會叫用它來合併兩個的執行緒-本機子運算的函式物件類型。

*_FnCombine*<br/>
用來結合子計算仿函式。 其簽章`T (T, T)`或`T (const T&, const T&)`，而且它必須是關聯式和交換式。

### <a name="return-value"></a>傳回值

合併所有執行緒私用子運算的最終結果。

##  <a name="combine_each"></a> combine_each

藉由呼叫執行緒區域子計算每一次提供的結合仿函式會計算最終的值從執行緒-本機子運算的集合。 最後的結果會累積函式物件。

```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>參數

*_Function*<br/>
會叫用它來合併單一執行緒區域子計算的函式物件類型。

*_FnCombine*<br/>
用來結合一個子計算仿函式。 其簽章`void (T)`或`void (const T&)`，而且必須是關聯式和交換式。

##  <a name="local"></a> 本機

傳回執行緒私用子運算的參考。

```
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>參數

*_Exists*<br/>
布林值的參考。 這個引數所參考的布林值會設定為**真**如果子計算已經存在於這個執行緒上，且設定為**false**如果這是在此執行緒的第一個子計算。

### <a name="return-value"></a>傳回值

執行緒私用子計算參考。

##  <a name="operator_eq"></a> 運算子 =

將指派給`combinable`物件從另一個`combinable`物件。

```
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>參數

*（_c)*<br/>
將現有`combinable`要複製到這個物件。

### <a name="return-value"></a>傳回值

此參考`combinable`物件。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
