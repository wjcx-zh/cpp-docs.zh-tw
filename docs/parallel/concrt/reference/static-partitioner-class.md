---
title: static_partitioner 類別
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: 7a58daa27bc7a2f51f78a3068a2f152979ffdd72
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142685"
---
# <a name="static_partitioner-class"></a>static_partitioner 類別

`static_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 此分割區會將範圍分成多個區塊，因為有背景工作角色可供基礎排程器使用。

## <a name="syntax"></a>語法

```cpp
class static_partitioner;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[static_partitioner](#ctor)|建構 `static_partitioner` 物件。|
|[~ static_partitioner 的析構函式](#dtor)|終結 `static_partitioner` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`static_partitioner`

## <a name="requirements"></a>需求

**標頭：** ppl。h

**命名空間：** concurrency

## <a name="dtor"></a>~ static_partitioner

終結 `static_partitioner` 物件。

```cpp
~static_partitioner();
```

## <a name="ctor"></a>static_partitioner

建構 `static_partitioner` 物件。

```cpp
static_partitioner();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
