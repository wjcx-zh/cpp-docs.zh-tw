---
title: event 類別
ms.date: 11/04/2016
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 2c72b4b086e932f4fe404259c25f8d2c8be2be31
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138850"
---
# <a name="event-class"></a>event 類別

其為並行執行階段明確察覺的手動重設事件。

## <a name="syntax"></a>語法

```cpp
class event;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[~ 事件的析構函式](#dtor)|終結事件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[reset](#reset)|將事件重設為未收到信號的狀態。|
|[set](#set)|對事件發出信號。|
|[等候](#wait)|等待事件變成信號。|
|[wait_for_multiple](#wait_for_multiple)|等候多個事件被通知。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|值，表示等候應該永遠不會逾時。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`event`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>發生

構造新的事件。

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>備註

## <a name="dtor"></a>~ 事件

終結事件。

```cpp
~event();
```

### <a name="remarks"></a>備註

當析構函式執行時，預期沒有線程在等候事件。 允許事件解構仍在等候的執行緒，會導致未定義的行為發生。

## <a name="reset"></a>啟動

將事件重設為未收到信號的狀態。

```cpp
void reset();
```

## <a name="set"></a>設定

對事件發出信號。

```cpp
void set();
```

### <a name="remarks"></a>備註

發出事件訊號會使事件上正在等候的任意數目內容變為可執行。

## <a name="timeout_infinite"></a>timeout_infinite

值，表示等候應該永遠不會逾時。

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a>等候

等待事件變成信號。

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_Timeout*<br/>
指出等待時間之前的毫秒數。值 `COOPERATIVE_TIMEOUT_INFINITE` 表示沒有超時。

### <a name="return-value"></a>傳回值

如果已滿足等候，則會傳回 `0` 的值;否則，此值會 `COOPERATIVE_WAIT_TIMEOUT`，以指出等待時間已超時，而沒有事件發出信號。

> [!IMPORTANT]
> 在通用 Windows 平臺（UWP）應用程式中，請勿在 ASTA 執行緒上呼叫 `wait`，因為此呼叫會封鎖目前的執行緒，而且可能會導致應用程式沒有回應。

## <a name="wait_for_multiple"></a>wait_for_multiple

等候多個事件被通知。

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_PPEvents*<br/>
要等候的事件陣列。 陣列內的事件數目是以 `count` 參數表示。

*計數*<br/>
`_PPEvents` 參數中提供之陣列內的事件計數。

*_FWaitAll*<br/>
如果設定為**true**值，則參數會指定在 `_PPEvents` 參數中提供的陣列內的所有事件都必須收到信號，才能滿足等候。 如果設定為**false**值，它會指定在 `_PPEvents` 參數中提供的陣列內的任何事件變成信號，將可滿足等候。

*_Timeout*<br/>
指出等待時間之前的毫秒數。值 `COOPERATIVE_TIMEOUT_INFINITE` 表示沒有超時。

### <a name="return-value"></a>傳回值

如果已滿足等候，則會在滿足等候條件的 `_PPEvents` 參數中提供陣列內的索引。否則，`COOPERATIVE_WAIT_TIMEOUT` 的值，表示等待時間沒有符合條件。

### <a name="remarks"></a>備註

如果參數 `_FWaitAll` 設定為值 `true` 以指出所有事件都必須收到信號以滿足等候，則函式所傳回的索引除了不是值 `COOPERATIVE_WAIT_TIMEOUT`的事實外，不會攜帶任何特殊的意義。

> [!IMPORTANT]
> 在通用 Windows 平臺（UWP）應用程式中，請勿在 ASTA 執行緒上呼叫 `wait_for_multiple`，因為此呼叫會封鎖目前的執行緒，而且可能會導致應用程式沒有回應。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
