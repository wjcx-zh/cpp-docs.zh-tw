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
ms.openlocfilehash: 18fabd0e741c144201f299271cdd01eb9ac55fac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222676"
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
要儲存在中的區塊資料類型 `network_link_registry` 。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`const_pointer`|一種類型，提供 **`const`** 物件中元素的指標 `network_link_registry` 。|
|`const_reference`|一種類型，提供 **`const`** 儲存在物件中以 `network_link_registry` 供讀取和執行 const 運算之元素的參考。|
|`iterator`|一種類型，提供可讀取或修改物件中任何元素的反覆運算器 `network_link_registry` 。|
|`type`|類型，表示儲存在物件中的區塊類型 `network_link_registry` 。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[add](#add)|在衍生類別中覆寫時，加入物件的連結 `network_link_registry` 。|
|[起點](#begin)|在衍生類別中覆寫時，將反覆運算器傳回物件中的第一個元素 `network_link_registry` 。|
|[contains](#contains)|在衍生類別中覆寫時，搜尋 `network_link_registry` 物件中是否有指定的區塊。|
|[計數](#count)|在衍生類別中覆寫時，傳回物件中的專案數 `network_link_registry` 。|
|[remove](#remove)|在衍生類別中覆寫時，從物件中移除指定的區塊 `network_link_registry` 。|

## <a name="remarks"></a>備註

`network link registry`不安全的平行存取。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`network_link_registry`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="add"></a><a name="add"></a>載入

在衍生類別中覆寫時，加入物件的連結 `network_link_registry` 。

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入之區塊的指標。

## <a name="begin"></a><a name="begin"></a>起點

在衍生類別中覆寫時，將反覆運算器傳回物件中的第一個元素 `network_link_registry` 。

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>傳回值

反覆運算器，定址物件中的第一個元素 `network_link_registry` 。

### <a name="remarks"></a>備註

反覆運算器的結束狀態會以 `NULL` 連結表示。

## <a name="contains"></a><a name="contains"></a>包含

在衍生類別中覆寫時，搜尋 `network_link_registry` 物件中是否有指定的區塊。

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>參數

*_Link*<br/>
要在物件中搜尋之區塊的指標 `network_link_registry` 。

### <a name="return-value"></a>傳回值

**`true`** 如果找到區塊，則 **`false`** 為，否則為。

## <a name="count"></a><a name="count"></a>計數

在衍生類別中覆寫時，傳回物件中的專案數 `network_link_registry` 。

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>傳回值

`network_link_registry` 物件中的項目數。

## <a name="remove"></a><a name="remove"></a>取消

在衍生類別中覆寫時，從物件中移除指定的區塊 `network_link_registry` 。

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除之區塊的指標（如有找到）。

### <a name="return-value"></a>傳回值

**`true`** 如果已找到並移除連結，則 **`false`** 為，否則為。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[single_link_registry 類別](single-link-registry-class.md)<br/>
[multi_link_registry 類別](multi-link-registry-class.md)
