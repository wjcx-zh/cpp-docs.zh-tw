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
ms.openlocfilehash: 89e6d972fbecb2674e6343bf6d11f9972c25c63d
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975043"
---
# <a name="tilebarrier-class"></a>tile_barrier 類別

同步處理在執行緒群組 (tile) 中執行所使用的執行緒的執行`wait`方法。 只有在執行階段可以具現化這個類別。

### <a name="syntax"></a>語法

```
class tile_barrier;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[tile_barrier 建構函式](#ctor)|初始化 `tile_barrier` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[wait](#wait)|指示要停止執行，直至 tile 中的所有執行緒均已都完成等待執行緒群組 (tile) 中的所有執行緒。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|封鎖執行，直到所有記憶體存取都已經都完成的所有執行緒和 tile 中的所有執行緒到達這個呼叫為止。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|封鎖直到所有全域記憶體存取的所有執行緒的執行已經完成，且 tile 中的所有執行緒都到達這個呼叫為止。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|封鎖 tile 中的所有執行緒的執行，直到所有`tile_static`記憶體存取已經完成，且 tile 中的所有執行緒都到達這個呼叫為止。|

## <a name="inheritance-hierarchy"></a>繼承階層

`tile_barrier`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="ctor"></a>  tile_barrier 建構函式

藉由複製現有初始化類別的新執行個體。

### <a name="syntax"></a>語法

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`tile_barrier`来複製的物件。

## <a name="wait"></a>等候

指示來停止執行，直到磚中的所有執行緒均已都完成等待執行緒群組 (tile) 中的所有執行緒。

### <a name="syntax"></a>語法

```
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a> wait_with_all_memory_fence

封鎖執行的所有執行緒，直到 tile 中的所有執行緒都到達這個呼叫為止。 這可確保所有記憶體存取對執行緒 tile 中，在其他執行緒可見，而且依照程式順序執行。

### <a name="syntax"></a>語法

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewaitwithglobalmemoryfence-waitwithglobalmemoryfence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

封鎖執行的所有執行緒，直到 tile 中的所有執行緒都到達這個呼叫為止。 這可確保所有全域記憶體存取對執行緒 tile 中，在其他執行緒可見，並已依照程式順序執行。

### <a name="syntax"></a>語法

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewaitwithtilestaticmemoryfence-waitwithtilestaticmemoryfence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

封鎖執行的所有執行緒，直到 tile 中的所有執行緒都到達這個呼叫為止。 這可確保`tile_static`記憶體存取對執行緒 tile 中，在其他執行緒可見，而且已依照程式順序執行。

### <a name="syntax"></a>語法

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
