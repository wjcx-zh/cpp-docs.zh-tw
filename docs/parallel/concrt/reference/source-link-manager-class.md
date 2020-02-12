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
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142702"
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

|名稱|描述|
|----------|-----------------|
|`const_pointer`|一種類型，提供 `source_link_manager` 物件中 `const` 元素的指標。|
|`const_reference`|一種類型，提供儲存在 `source_link_manager` 物件中之 `const` 專案的參考，以便讀取和執行 const 運算。|
|`iterator`|一種類型，提供可讀取或修改 `source_link_manager` 物件中任何元素的反覆運算器。|
|`type`|由 `source_link_manager` 物件所管理的連結登錄類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[source_link_manager](#ctor)|建構 `source_link_manager` 物件。|
|[~ source_link_manager 的析構函式](#dtor)|終結 `source_link_manager` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[add](#add)|將來源連結新增至 `source_link_manager` 物件。|
|[begin](#begin)|將反覆運算器傳回至 `source_link_manager` 物件中的第一個元素。|
|[contains](#contains)|在這個 `source_link_manager` 物件內搜尋指定區塊的 `network_link_registry`。|
|[計數](#count)|計算 `source_link_manager` 物件中連結區塊的數目。|
|[reference](#reference)|取得 `source_link_manager` 物件的參考。|
|[register_target_block](#register_target_block)|註冊保存此 `source_link_manager` 物件的目標區塊。|
|[release](#release)|釋放 `source_link_manager` 物件的參考。|
|[remove](#remove) \(英文\)|從 `source_link_manager` 物件移除連結。|
|[set_bound](#set_bound)|設定可新增至此 `source_link_manager` 物件的來源連結數目上限。|

## <a name="remarks"></a>備註

目前，來源區塊會進行參考計數。 這是 `network_link_registry` 物件上的包裝函式，允許平行存取連結，並提供透過回呼來參考連結的功能。 訊息區塊（`target_block`s 或 `propagator_block`s）應使用此類別作為其來源連結。

## <a name="inheritance-hierarchy"></a>繼承階層

`source_link_manager`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="add"></a>載入

將來源連結新增至 `source_link_manager` 物件。

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入之區塊的指標。

## <a name="begin"></a>起點

將反覆運算器傳回至 `source_link_manager` 物件中的第一個元素。

```cpp
iterator begin();
```

### <a name="return-value"></a>傳回值

反覆運算器，定址物件是 `source_link_manager` 物件中的第一個元素。

### <a name="remarks"></a>備註

反覆運算器的結束狀態是以 `NULL` 連結來表示。

## <a name="contains"></a>包含

在這個 `source_link_manager` 物件內搜尋指定區塊的 `network_link_registry`。

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要在 `source_link_manager` 物件中搜尋之區塊的指標。

### <a name="return-value"></a>傳回值

如果找到指定的區塊，**則為 true** ，否則為**false** 。

## <a name="count"></a>計數

計算 `source_link_manager` 物件中連結區塊的數目。

```cpp
size_t count();
```

### <a name="return-value"></a>傳回值

`source_link_manager` 物件中的連結區塊數目。

## <a name="reference"></a>證明

取得 `source_link_manager` 物件的參考。

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

註冊保存此 `source_link_manager` 物件的目標區塊。

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
保存此 `source_link_manager` 物件的目標區塊。

## <a name="release"></a>版本

釋放 `source_link_manager` 物件的參考。

```cpp
void release();
```

## <a name="remove"></a>取消

從 `source_link_manager` 物件移除連結。

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除之區塊的指標（如有找到）。

### <a name="return-value"></a>傳回值

如果找到並移除連結，**則為 true** ，否則為**false** 。

## <a name="set_bound"></a>set_bound

設定可新增至此 `source_link_manager` 物件的來源連結數目上限。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>參數

*_MaxLinks*<br/>
連結的最大數目。

## <a name="ctor"></a>source_link_manager

建構 `source_link_manager` 物件。

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

終結 `source_link_manager` 物件。

```cpp
~source_link_manager();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[single_link_registry 類別](single-link-registry-class.md)<br/>
[multi_link_registry 類別](multi-link-registry-class.md)
