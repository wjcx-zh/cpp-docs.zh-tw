---
title: event 類別
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 3f2ec71083f7a7905bad5cda014baba914e31e79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215799"
---
# <a name="event-class"></a>event 類別

其為並行執行階段明確察覺的手動重設事件。

## <a name="syntax"></a>語法

```cpp
class event;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[~ 事件的析構函式](#dtor)|終結事件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[reset](#reset)|將事件重設為未收到信號的狀態。|
|[set](#set)|對事件發出信號。|
|[等候](#wait)|等待事件變成信號。|
|[wait_for_multiple](#wait_for_multiple)|等候多個事件被通知。|

### <a name="public-constants"></a>公用常數

|名稱|說明|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|值，表示等候應該永遠不會逾時。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`event`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** 並行

## <a name="event"></a><a name="ctor"></a> 事件

構造新的事件。

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>備註

## <a name="event"></a><a name="dtor"></a>~ 事件

終結事件。

```cpp
~event();
```

### <a name="remarks"></a>備註

當析構函式執行時，預期沒有線程在等候事件。 允許事件解構仍在等候的執行緒，會導致未定義的行為發生。

## <a name="reset"></a><a name="reset"></a>啟動

將事件重設為未收到信號的狀態。

```cpp
void reset();
```

## <a name="set"></a><a name="set"></a>設定

對事件發出信號。

```cpp
void set();
```

### <a name="remarks"></a>備註

發出事件訊號會使事件上正在等候的任意數目內容變為可執行。

## <a name="timeout_infinite"></a><a name="timeout_infinite"></a>timeout_infinite

值，表示等候應該永遠不會逾時。

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a><a name="wait"></a>等候

等待事件變成信號。

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_Timeout*<br/>
指出等待時間之前的毫秒數。值 `COOPERATIVE_TIMEOUT_INFINITE` 表示沒有超時。

### <a name="return-value"></a>傳回值

如果已滿足等候，則 `0` 會傳回值，否則會傳回值， `COOPERATIVE_WAIT_TIMEOUT` 以指出等待時間已超時，而沒有事件信號。

> [!IMPORTANT]
> 在通用 Windows 平臺（UWP）應用程式中，請勿 `wait` 在 ASTA 執行緒上呼叫，因為此呼叫會封鎖目前的執行緒，而且可能會導致應用程式沒有回應。

## <a name="wait_for_multiple"></a><a name="wait_for_multiple"></a>wait_for_multiple

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
在參數中提供之陣列內的事件計數 `_PPEvents` 。

*_FWaitAll*<br/>
如果設定為值 **`true`** ，參數就會指定參數中提供之陣列內的所有事件都 `_PPEvents` 必須收到信號，才能滿足等候。 如果設定為值 **`false`** ，它會指定在參數中提供的任何事件 `_PPEvents` 變成信號，以符合等待。

*_Timeout*<br/>
指出等待時間之前的毫秒數。值 `COOPERATIVE_TIMEOUT_INFINITE` 表示沒有超時。

### <a name="return-value"></a>傳回值

如果已滿足等候，則為符合等候條件之參數中所提供的陣列內的索引， `_PPEvents` 否則為值， `COOPERATIVE_WAIT_TIMEOUT` 表示等待時間未滿足條件。

### <a name="remarks"></a>備註

如果參數 `_FWaitAll` 設定為值， **`true`** 指出所有事件都必須收到信號以滿足等候，則函式所傳回的索引除了不是值以外，不會攜帶任何特殊的重要性 `COOPERATIVE_WAIT_TIMEOUT` 。

> [!IMPORTANT]
> 在通用 Windows 平臺（UWP）應用程式中，請勿 `wait_for_multiple` 在 ASTA 執行緒上呼叫，因為此呼叫會封鎖目前的執行緒，而且可能會導致應用程式沒有回應。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
