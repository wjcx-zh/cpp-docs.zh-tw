---
title: auto_partitioner 類別
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 4d1d8f19069412240de8e9d69cdcfb34618f2796
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142871"
---
# <a name="auto_partitioner-class"></a>auto_partitioner 類別

`auto_partitioner` 類別表示 `parallel_for`、`parallel_for_each` 和 `parallel_transform` 用來分割其逐一查看之範圍的預設方法。 這種資料分割方法會採用範圍竊取來進行負載平衡，以及按逐一查看取消。

## <a name="syntax"></a>語法

```cpp
class auto_partitioner;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[auto_partitioner](#ctor)|建構 `auto_partitioner` 物件。|
|[~ auto_partitioner 的析構函式](#dtor)|終結 `auto_partitioner` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`auto_partitioner`

## <a name="requirements"></a>需求

**標頭：** ppl。h

**命名空間：** concurrency

## <a name="dtor"></a>~ auto_partitioner

終結 `auto_partitioner` 物件。

```cpp
~auto_partitioner();
```

## <a name="ctor"></a>auto_partitioner

建構 `auto_partitioner` 物件。

```cpp
auto_partitioner();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
