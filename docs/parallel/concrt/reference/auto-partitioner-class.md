---
title: auto_partitioner 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2bb62d76733e77c2528a80dfc4e9ef358878895
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425396"
---
# <a name="autopartitioner-class"></a>auto_partitioner 類別

`auto_partitioner` 類別表示 `parallel_for`、`parallel_for_each` 和 `parallel_transform` 用來分割其逐一查看之範圍的預設方法。 這種分割方法會使用範圍竊取，來進行負載平衡及逐一查看取消作業。

## <a name="syntax"></a>語法

```
class auto_partitioner;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[auto_partitioner](#ctor)|建構 `auto_partitioner` 物件。|
|[~ auto_partitioner 解構函式](#dtor)|終結 `auto_partitioner` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`auto_partitioner`

## <a name="requirements"></a>需求

**標頭：** ppl.h

**命名空間：** concurrency

##  <a name="dtor"></a> ~auto_partitioner

終結 `auto_partitioner` 物件。

```
~auto_partitioner();
```

##  <a name="ctor"></a> auto_partitioner

建構 `auto_partitioner` 物件。

```
auto_partitioner();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
