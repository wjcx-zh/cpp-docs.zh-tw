---
title: tile_barrier 類別
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855909"
---
# <a name="tile_barrier-class"></a>tile_barrier 類別

使用 `wait` 方法，同步處理執行緒群組（磚）中執行的執行緒。 只有執行時間可以具現化此類別。

## <a name="syntax"></a>語法

```cpp
class tile_barrier;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tile_barrier 的構造函式](#ctor)|初始化 `tile_barrier` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[等候](#wait)|指示執行緒群組（磚）中的所有線程停止執行，直到磚中的所有線程都完成等候為止。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|封鎖磚中所有線程的執行，直到所有記憶體存取都完成，而且磚中的所有線程都已達到此呼叫。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|封鎖磚中所有線程的執行，直到所有全域記憶體存取都完成，而且磚中的所有線程都已達到此呼叫。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|封鎖磚中所有線程的執行，直到所有 `tile_static` 記憶體存取都完成，而且磚中的所有線程都已達到此呼叫。|

## <a name="inheritance-hierarchy"></a>繼承階層

`tile_barrier`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="ctor"></a>tile_barrier 的構造函式

藉由複製現有的實例，初始化類別的新實例。

### <a name="syntax"></a>語法

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的 `tile_barrier` 物件。

## <a name="wait"></a>wait

指示執行緒群組（磚）中的所有線程停止執行，直到磚中的所有線程都完成等候為止。

### <a name="syntax"></a>語法

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

封鎖磚中所有線程的執行，直到磚中的所有線程都達到此呼叫為止。 這可確保執行緒磚中的其他執行緒都可以看到所有的記憶體存取，並已依照程式循序執行。

### <a name="syntax"></a>語法

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

封鎖磚中所有線程的執行，直到磚中的所有線程都達到此呼叫為止。 這可確保 [執行緒] 磚中的其他執行緒可以看見所有全域記憶體存取，而且已依照程式循序執行。

### <a name="syntax"></a>語法

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

封鎖磚中所有線程的執行，直到磚中的所有線程都達到此呼叫為止。 這可確保執行緒磚中的其他執行緒可以看到 `tile_static` 的記憶體存取，並已依照程式循序執行。

### <a name="syntax"></a>語法

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
