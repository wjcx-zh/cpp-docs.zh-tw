---
title: network_link_registry 類別
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138881"
---
# <a name="network_link_registry-class"></a>network_link_registry 類別

`network_link_registry` 抽象基底類別會管理來源和目標區塊之間的連結。

## <a name="syntax"></a>語法

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>參數

*_Block*<br/>
儲存在 `network_link_registry`中的區塊資料類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`const_pointer`|一種類型，提供 `network_link_registry` 物件中 `const` 元素的指標。|
|`const_reference`|一種類型，提供儲存在 `network_link_registry` 物件中之 `const` 專案的參考，以便讀取和執行 const 運算。|
|`iterator`|一種類型，提供可讀取或修改 `network_link_registry` 物件中任何元素的反覆運算器。|
|`type`|類型，表示儲存在 `network_link_registry` 物件中的區塊類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[add](#add)|在衍生類別中覆寫時，加入 `network_link_registry` 物件的連結。|
|[begin](#begin)|在衍生類別中覆寫時，將反覆運算器傳回至 `network_link_registry` 物件中的第一個元素。|
|[contains](#contains)|在衍生類別中覆寫時，搜尋指定區塊的 `network_link_registry` 物件。|
|[計數](#count)|在衍生類別中覆寫時，傳回 `network_link_registry` 物件中的專案數。|
|[remove](#remove) \(英文\)|在衍生類別中覆寫時，從 `network_link_registry` 物件中移除指定的區塊。|

## <a name="remarks"></a>備註

針對平行存取，`network link registry` 是不安全的。

## <a name="inheritance-hierarchy"></a>繼承階層

`network_link_registry`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="add"></a>載入

在衍生類別中覆寫時，加入 `network_link_registry` 物件的連結。

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入之區塊的指標。

## <a name="begin"></a>起點

在衍生類別中覆寫時，將反覆運算器傳回至 `network_link_registry` 物件中的第一個元素。

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>傳回值

反覆運算器，定址物件是 `network_link_registry` 物件中的第一個元素。

### <a name="remarks"></a>備註

反覆運算器的結束狀態是以 `NULL` 連結來表示。

## <a name="contains"></a>包含

在衍生類別中覆寫時，搜尋指定區塊的 `network_link_registry` 物件。

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>參數

*_Link*<br/>
要在 `network_link_registry` 物件中搜尋之區塊的指標。

### <a name="return-value"></a>傳回值

如果找到區塊，**則為 true** ，否則為**false** 。

## <a name="count"></a>計數

在衍生類別中覆寫時，傳回 `network_link_registry` 物件中的專案數。

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>傳回值

`network_link_registry` 物件中的項目數。

## <a name="remove"></a>取消

在衍生類別中覆寫時，從 `network_link_registry` 物件中移除指定的區塊。

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除之區塊的指標（如有找到）。

### <a name="return-value"></a>傳回值

如果找到並移除連結，**則為 true** ，否則為**false** 。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[single_link_registry 類別](single-link-registry-class.md)<br/>
[multi_link_registry 類別](multi-link-registry-class.md)
