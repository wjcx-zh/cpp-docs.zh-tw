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
ms.openlocfilehash: c00f1e41e70e723be185959eeff176390def7647
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374718"
---
# <a name="tile_barrier-class"></a>tile_barrier 類別

使用`wait`方法同步線程組(磁貼)中正在運行的線程的執行。 只有運行時才能實例化此類。

## <a name="syntax"></a>語法

```cpp
class tile_barrier;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tile_barrier建構函數](#ctor)|將 `tile_barrier` 類別的新執行個體初始化。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[等](#wait)|指示線程組(磁貼)中的所有線程停止執行,直到磁貼中的所有線程都已完成等待。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|阻止執行磁貼中的所有線程,直到完成所有記憶體訪問並且磁貼中的所有線程都達到此調用。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|阻止執行磁貼中的所有線程,直到完成所有全域記憶體訪問並且磁貼中的所有線程都已達到此調用。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|阻止執行磁貼中的所有線程,直到完成所有`tile_static`記憶體訪問並且磁貼中的所有線程都達到此調用。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tile_barrier`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="tile_barrier-constructor"></a><a name="ctor"></a>tile_barrier建構函數

通過複製現有類的新實例來初始化該類的新實例。

### <a name="syntax"></a>語法

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的 `tile_barrier` 物件。

## <a name="wait"></a>wait

指示線程組(切片)中的所有線程停止執行,直到磁貼中的所有線程都已完成等待。

### <a name="syntax"></a>語法

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

阻止執行磁貼中的所有線程,直到磁貼中的所有線程都達到此調用。 這可確保線程磁貼中的其他線程對所有記憶體訪問都可見,並且已按程式順序執行。

### <a name="syntax"></a>語法

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence">wait_with_global_memory_fence

阻止執行磁貼中的所有線程,直到磁貼中的所有線程都達到此調用。 這可確保線程磁貼中的其他線程對所有全域記憶體訪問都可見,並且已按程式順序執行。

### <a name="syntax"></a>語法

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence">wait_with_tile_static_memory_fence

阻止執行磁貼中的所有線程,直到磁貼中的所有線程都達到此調用。 這可確保`tile_static`記憶體訪問對線程磁貼中的其他線程可見,並且已按程式順序執行。

### <a name="syntax"></a>語法

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)
