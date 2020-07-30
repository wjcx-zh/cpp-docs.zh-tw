---
title: multi_link_registry 類別
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: 777b3f5206b4a595b5dcac653d608255e92f4ef6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231698"
---
# <a name="multi_link_registry-class"></a>multi_link_registry 類別

`multi_link_registry` 物件是管理多個來源區塊或多個目標區塊的 `network_link_registry`。

## <a name="syntax"></a>語法

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>參數

*_Block*<br/>
要儲存在物件中的區塊資料類型 `multi_link_registry` 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[multi_link_registry](#ctor)|建構 `multi_link_registry` 物件。|
|[~ multi_link_registry 的析構函式](#dtor)|終結 `multi_link_registry` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[add](#add)|將連結加入至 `multi_link_registry` 物件。 （覆寫[network_link_registry：： add](network-link-registry-class.md#add)。）|
|[起點](#begin)|將反覆運算器傳回物件中的第一個元素 `multi_link_registry` 。 （覆寫[network_link_registry：： begin](network-link-registry-class.md#begin)。）|
|[contains](#contains)|搜尋 `multi_link_registry` 物件中是否有指定的區塊。 （覆寫[network_link_registry：： contains](network-link-registry-class.md#contains)。）|
|[計數](#count)|計算物件中的專案數 `multi_link_registry` 。 （覆寫[network_link_registry：： count](network-link-registry-class.md#count)。）|
|[remove](#remove)|從物件中移除連結 `multi_link_registry` 。 （覆寫[network_link_registry：： remove](network-link-registry-class.md#remove)。）|
|[set_bound](#set_bound)|設定物件可以保存之連結數目的上限 `multi_link_registry` 。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="add"></a><a name="add"></a>載入

將連結加入至 `multi_link_registry` 物件。

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入之區塊的指標。

### <a name="remarks"></a>備註

如果連結已存在於登錄中，或如果已使用函式設定系結，且連結已被移除，方法會擲回[invalid_link_target](invalid-link-target-class.md)例外狀況 `set_bound` 。

## <a name="begin"></a><a name="begin"></a>起點

將反覆運算器傳回物件中的第一個元素 `multi_link_registry` 。

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>傳回值

反覆運算器，定址物件中的第一個元素 `multi_link_registry` 。

### <a name="remarks"></a>備註

結束狀態會以 `NULL` 連結表示。

## <a name="contains"></a><a name="contains"></a>包含

搜尋 `multi_link_registry` 物件中是否有指定的區塊。

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要在物件中搜尋之區塊的指標 `multi_link_registry` 。

### <a name="return-value"></a>傳回值

**`true`** 如果找到指定的區塊，則 **`false`** 為，否則為。

## <a name="count"></a><a name="count"></a>計數

計算物件中的專案數 `multi_link_registry` 。

```cpp
virtual size_t count();
```

### <a name="return-value"></a>傳回值

`multi_link_registry` 物件中的項目數。

## <a name="multi_link_registry"></a><a name="ctor"></a>multi_link_registry

建構 `multi_link_registry` 物件。

```cpp
multi_link_registry();
```

## <a name="multi_link_registry"></a><a name="dtor"></a>~ multi_link_registry

終結 `multi_link_registry` 物件。

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>備註

如果在移除所有連結之前呼叫，方法會擲回[invalid_operation](invalid-operation-class.md)例外狀況。

## <a name="remove"></a><a name="remove"></a>取消

從物件中移除連結 `multi_link_registry` 。

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除之區塊的指標（如有找到）。

### <a name="return-value"></a>傳回值

**`true`** 如果已找到並移除連結，則 **`false`** 為，否則為。

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

設定物件可以保存之連結數目的上限 `multi_link_registry` 。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>參數

*_MaxLinks*<br/>
物件可以保存的最大連結數 `multi_link_registry` 。

### <a name="remarks"></a>備註

繫結設定後，取消連結項目將導致 `multi_link_registry` 物件進入不可變的狀態，後續在這種狀態下呼叫 `add` 將會擲回 `invalid_link_target` 例外狀況。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[single_link_registry 類別](single-link-registry-class.md)
