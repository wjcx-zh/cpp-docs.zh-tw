---
title: single_link_registry 類別
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142727"
---
# <a name="single_link_registry-class"></a>single_link_registry 類別

`single_link_registry` 物件是只管理單一來源或目標區塊的 `network_link_registry`。

## <a name="syntax"></a>語法

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>參數

*_Block*<br/>
要儲存在 `single_link_registry` 物件中的區塊資料類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[single_link_registry](#ctor)|建構 `single_link_registry` 物件。|
|[~ single_link_registry 的析構函式](#dtor)|終結 `single_link_registry` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[add](#add)|加入 `single_link_registry` 物件的連結。 （覆寫[network_link_registry：： add](network-link-registry-class.md#add)。）|
|[begin](#begin)|將反覆運算器傳回至 `single_link_registry` 物件中的第一個元素。 （覆寫[network_link_registry：： begin](network-link-registry-class.md#begin)。）|
|[contains](#contains)|在 `single_link_registry` 物件中搜尋指定的區塊。 （覆寫[network_link_registry：： contains](network-link-registry-class.md#contains)。）|
|[計數](#count)|計算 `single_link_registry` 物件中的專案數。 （覆寫[network_link_registry：： count](network-link-registry-class.md#count)。）|
|[remove](#remove) \(英文\)|從 `single_link_registry` 物件移除連結。 （覆寫[network_link_registry：： remove](network-link-registry-class.md#remove)。）|

## <a name="inheritance-hierarchy"></a>繼承階層

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="add"></a>載入

加入 `single_link_registry` 物件的連結。

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入之區塊的指標。

### <a name="remarks"></a>備註

如果此登錄中已經有連結，方法會擲回[invalid_link_target](invalid-link-target-class.md)例外狀況。

## <a name="begin"></a>起點

將反覆運算器傳回至 `single_link_registry` 物件中的第一個元素。

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>傳回值

反覆運算器，定址物件是 `single_link_registry` 物件中的第一個元素。

### <a name="remarks"></a>備註

結束狀態會以 `NULL` 連結來表示。

## <a name="contains"></a>包含

在 `single_link_registry` 物件中搜尋指定的區塊。

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要在 `single_link_registry` 物件中搜尋之區塊的指標。

### <a name="return-value"></a>傳回值

如果找到連結，**則為 true** ，否則為**false** 。

## <a name="count"></a>計數

計算 `single_link_registry` 物件中的專案數。

```cpp
virtual size_t count();
```

### <a name="return-value"></a>傳回值

`single_link_registry` 物件中的項目數。

## <a name="remove"></a>取消

從 `single_link_registry` 物件移除連結。

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除之區塊的指標（如有找到）。

### <a name="return-value"></a>傳回值

如果找到並移除連結，**則為 true** ，否則為**false** 。

## <a name="ctor"></a>single_link_registry

建構 `single_link_registry` 物件。

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

終結 `single_link_registry` 物件。

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>備註

如果在移除連結之前呼叫此方法，則會擲回[invalid_operation](invalid-operation-class.md)例外狀況。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[multi_link_registry 類別](multi-link-registry-class.md)
