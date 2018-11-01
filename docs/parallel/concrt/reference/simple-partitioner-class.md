---
title: simple_partitioner 類別
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: f3c5792a13d9e63a05ce6710dea77828f2510f0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522443"
---
# <a name="simplepartitioner-class"></a>simple_partitioner 類別

`simple_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 Partitioner 會將這個範圍分割成區塊，每個區塊都有由區塊大小指定之反覆項目的最少次數。

## <a name="syntax"></a>語法

```
class simple_partitioner;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[simple_partitioner](#ctor)|建構 `simple_partitioner` 物件。|
|[~ simple_partitioner 解構函式](#dtor)|終結 `simple_partitioner` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`simple_partitioner`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="dtor"></a> ~simple_partitioner

終結 `simple_partitioner` 物件。

```
~simple_partitioner();
```

##  <a name="ctor"></a> simple_partitioner

建構 `simple_partitioner` 物件。

```
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>參數

*_Chunk_size*<br/>
最小分割區大小。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
