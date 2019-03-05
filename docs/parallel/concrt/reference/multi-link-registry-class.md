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
ms.openlocfilehash: 388cc0082f69041368d1a444179855451d552ce6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264754"
---
# <a name="multilinkregistry-class"></a>multi_link_registry 類別


  `multi_link_registry` 物件是管理多個來源區塊或多個目標區塊的 `network_link_registry`。

## <a name="syntax"></a>語法

```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

#### <a name="parameters"></a>參數

*_Block*<br/>
區塊資料類型儲存在`multi_link_registry`物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[multi_link_registry](#ctor)|建構 `multi_link_registry` 物件。|
|[~ multi_link_registry 解構函式](#dtor)|終結`multi_link_registry`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[add](#add)|新增連結`multi_link_registry`物件。 (覆寫[network_link_registry:: add](network-link-registry-class.md#add)。)|
|[begin](#begin)|傳回迭代器中的第一個項目`multi_link_registry`物件。 (覆寫[network_link_registry:: begin](network-link-registry-class.md#begin)。)|
|[contains](#contains)|搜尋`multi_link_registry`物件指定的區塊。 (覆寫[network_link_registry:: contains](network-link-registry-class.md#contains)。)|
|[count](#count)|計算中的項目數`multi_link_registry`物件。 (覆寫[network_link_registry:: count](network-link-registry-class.md#count)。)|
|[remove](#remove)|移除連結，以從`multi_link_registry`物件。 (覆寫[network_link_registry:: remove](network-link-registry-class.md#remove)。)|
|[set_bound](#set_bound)|連結的數目設定上限`multi_link_registry`物件可以保存。|

## <a name="inheritance-hierarchy"></a>繼承階層

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="add"></a> add

新增連結`multi_link_registry`物件。

```
virtual void add(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要加入的區塊的指標。

### <a name="remarks"></a>備註

方法會擲回[invalid_link_target](invalid-link-target-class.md)例外狀況的連結是否已經存在於登錄中，或如果已繫結已設定使用`set_bound`函式，並連結已被移除。

##  <a name="begin"></a> begin

傳回迭代器中的第一個項目`multi_link_registry`物件。

```
virtual iterator begin();
```

### <a name="return-value"></a>傳回值

迭代器中的第一個項目定址`multi_link_registry`物件。

### <a name="remarks"></a>備註

結束狀態會表示`NULL`連結。

##  <a name="contains"></a> 包含

搜尋`multi_link_registry`物件指定的區塊。

```
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要搜尋中的區塊的指標`multi_link_registry`物件。

### <a name="return-value"></a>傳回值

**真**找不到指定的區塊，如果**false**否則。

##  <a name="count"></a> count

計算中的項目數`multi_link_registry`物件。

```
virtual size_t count();
```

### <a name="return-value"></a>傳回值

中的項目數`multi_link_registry`物件。

##  <a name="ctor"></a> multi_link_registry

建構 `multi_link_registry` 物件。

```
multi_link_registry();
```

##  <a name="dtor"></a> ~multi_link_registry

終結`multi_link_registry`物件。

```
virtual ~multi_link_registry();
```

### <a name="remarks"></a>備註

方法會擲回[invalid_operation](invalid-operation-class.md)例外狀況，如果呼叫前會移除所有的連結。

##  <a name="remove"></a> 移除

移除連結，以從`multi_link_registry`物件。

```
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>參數

*_Link*<br/>
要移除，如果區塊的指標找到。

### <a name="return-value"></a>傳回值

**真**如果連結已找到並移除**false**否則。

##  <a name="set_bound"></a> set_bound

連結的數目設定上限`multi_link_registry`物件可以保存。

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>參數

*_MaxLinks*<br/>
最大數目的連結，`multi_link_registry`物件可以保存。

### <a name="remarks"></a>備註

繫結設定後，取消連結項目將導致 `multi_link_registry` 物件進入不可變的狀態，後續在這種狀態下呼叫 `add` 將會擲回 `invalid_link_target` 例外狀況。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[single_link_registry 類別](single-link-registry-class.md)
