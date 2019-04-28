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
ms.openlocfilehash: 5120e3c53dc00ba9d5c3a4218efe1dcfb8f92e28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337384"
---
# <a name="staticpartitioner-class"></a>static_partitioner 類別

`static_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 Partitioner 會將範圍分成許多區塊，其數量與基礎排程器可用的背景工作數量相等。

## <a name="syntax"></a>語法

```
class static_partitioner;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[static_partitioner](#ctor)|建構 `static_partitioner` 物件。|
|[~ static_partitioner 解構函式](#dtor)|終結 `static_partitioner` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`static_partitioner`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="dtor"></a> ~static_partitioner

終結 `static_partitioner` 物件。

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner

建構 `static_partitioner` 物件。

```
static_partitioner();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
