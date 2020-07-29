---
title: source_link_manager 類別
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 98f99bb5aec85a640eaf83a07fae3a1b667f7d91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228423"
---
# <a name="source_link_manager-class"></a>source_link_manager 類別

`source_link_manager` 物件會管理 `ISource` 區塊與傳訊區塊網路的連結。

## <a name="syntax"></a>語法

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>參數

*_LinkRegistry*<br/>
網路連結登錄。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|Name|說明|
|----------|-----------------|
|`const_pointer`|一種類型，提供 **`const`** 物件中元素的指標 `source_link_manager` 。|
|`const_reference`|一種類型，提供 **`const`** 儲存在物件中以 `source_link_manager` 供讀取和執行 const 運算之元素的參考。|
|`iterator`|一種類型，提供可讀取或修改物件中任何元素的反覆運算器 `source_link_manager` 。|
|`type`|由物件管理的連結登錄類型 `source_link_manager` 。|

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[source_link_manager](#ctor)|建構 `source_link_manager` 物件。|
|[~ source_link_manager 的析構函式](#dtor)|終結 `source_link_manager` 物件。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[add](#add)|將來源連結加入至 `source_link_manager` 物件。|
|[起點](#begin)|將反覆運算器傳回物件中的第一個元素 `source_link_manager` 。|
|[contains](#contains)|在 `network_link_registry` 這個物件內搜尋 `source_link_manager` 指定的區塊。|
|[計數](#count)|計算物件中連結區塊的數目 `source_link_manager` 。|
|[reference](#reference)|取得物件的參考 `source_link_manager` 。|
|[register_target_block](#register_target_block)|註冊保存此物件的目標區塊 `source_link_manager` 。|
|[版本](#release)|釋放物件的參考 `source_link_manager` 。|
|[remove](#remove)|從物件中移除連結 `source_link_manager` 。|
|[set_bound](#set_bound)|設定可新增至這個物件的來源連結數目上限 `source_link_manager` 。|

## <a name="remarks"></a>備註

目前，來源區塊會進行參考計數。 這是物件的包裝函式， `network_link_registry` 允許平行存取連結，並提供透過回呼來參考連結的功能。 訊息區塊（ `target_block` s 或 `propagator_block` s）應使用此類別作為其來源連結。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`source_link_manager`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="add"></a><a name="add"></a>載入

將來源連結加入至 `source_link_manager` 物件。

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入之區塊的指標。

## <a name="begin"></a><a name="begin"></a>起點

將反覆運算器傳回物件中的第一個元素 `source_link_manager` 。

```cpp
iterator begin();
```

### <a name="return-value"></a>傳回值

反覆運算器，定址物件中的第一個元素 `source_link_manager` 。

### <a name="remarks"></a>備註

反覆運算器的結束狀態會以 `NULL` 連結表示。

## <a name="contains"></a><a name="contains"></a>包含

在 `network_link_registry` 這個物件內搜尋 `source_link_manager` 指定的區塊。

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要在物件中搜尋之區塊的指標 `source_link_manager` 。

### <a name="return-value"></a>傳回值

**`true`** 如果找到指定的區塊，則 **`false`** 為，否則為。

## <a name="count"></a><a name="count"></a>計數

計算物件中連結區塊的數目 `source_link_manager` 。

```cpp
size_t count();
```

### <a name="return-value"></a>傳回值

物件中連結的區塊數目 `source_link_manager` 。

## <a name="reference"></a><a name="reference"></a>證明

取得物件的參考 `source_link_manager` 。

```cpp
void reference();
```

## <a name="register_target_block"></a><a name="register_target_block"></a>register_target_block

註冊保存此物件的目標區塊 `source_link_manager` 。

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
保存此物件的目標區塊 `source_link_manager` 。

## <a name="release"></a><a name="release"></a>版本

釋放物件的參考 `source_link_manager` 。

```cpp
void release();
```

## <a name="remove"></a><a name="remove"></a>取消

從物件中移除連結 `source_link_manager` 。

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除之區塊的指標（如有找到）。

### <a name="return-value"></a>傳回值

**`true`** 如果已找到並移除連結，則 **`false`** 為，否則為。

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

設定可新增至這個物件的來源連結數目上限 `source_link_manager` 。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>參數

*_MaxLinks*<br/>
連結的最大數目。

## <a name="source_link_manager"></a><a name="ctor"></a>source_link_manager

建構 `source_link_manager` 物件。

```cpp
source_link_manager();
```

## <a name="source_link_manager"></a><a name="dtor"></a>~ source_link_manager

終結 `source_link_manager` 物件。

```cpp
~source_link_manager();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[single_link_registry 類別](single-link-registry-class.md)<br/>
[multi_link_registry 類別](multi-link-registry-class.md)
