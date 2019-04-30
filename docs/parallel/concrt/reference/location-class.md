---
title: location 類別
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 5e90dd3b23b33f6699f2df4ce0df9178f95816b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375453"
---
# <a name="location-class"></a>location 類別

硬體實體位置的抽象概念。

## <a name="syntax"></a>語法

```
class location;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[location](#ctor)|多載。 建構 `location` 物件。|
|[~ location 解構函式](#dtor)|終結 `location` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[current](#current)|傳回 `location` 物件，表示呼叫執行緒執行的最特定位置。|
|[from_numa_node](#from_numa_node)|傳回 `location` 物件，該物件代表某一特定的 NUMA 節點。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](#operator_neq)|判斷兩個 `location` 物件是否表示不同的位置。|
|[operator=](#operator_eq)|將不同 `location` 物件的內容指派給這一個。|
|[operator==](#operator_eq_eq)|判斷兩個`location`物件代表相同的位置。|

## <a name="inheritance-hierarchy"></a>繼承階層

`location`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="dtor"></a> ~location

終結 `location` 物件。

```
~location();
```

##  <a name="current"></a> 目前

傳回 `location` 物件，表示呼叫執行緒執行的最特定位置。

```
static location __cdecl current();
```

### <a name="return-value"></a>傳回值

表示呼叫執行緒執行的最特定位置。

##  <a name="from_numa_node"></a> from_numa_node

傳回 `location` 物件，該物件代表某一特定的 NUMA 節點。

```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>參數

*_NumaNodeNumber*<br/>
要建構其位置的 NUMA 節點編號。

### <a name="return-value"></a>傳回值

代表 NUMA 節點的位置，由 `_NumaNodeNumber` 參數所指定。

##  <a name="ctor"></a> 位置

建構 `location` 物件。

```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>參數

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
（選擇性）繫結指標。

### <a name="remarks"></a>備註

預設建構的位置表示整個系統。

##  <a name="operator_neq"></a> 運算子 ！ =

判斷兩個 `location` 物件是否表示不同的位置。

```
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
運算元`location`。

### <a name="return-value"></a>傳回值

**真**如果兩個位置不同， **false**否則。

##  <a name="operator_eq"></a> 運算子 =

將不同 `location` 物件的內容指派給這一個。

```
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
來源 `location` 物件。

### <a name="return-value"></a>傳回值

##  <a name="operator_eq_eq"></a> 運算子 = =

判斷兩個`location`物件代表相同的位置。

```
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
運算元`location`。

### <a name="return-value"></a>傳回值

**真**如果兩個位置都相同，並**false**否則。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
