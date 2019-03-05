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
ms.openlocfilehash: aa9d46b868c1a31729a9590db3b3f67179903881
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264661"
---
# <a name="event-class"></a>event 類別

其為並行執行階段明確察覺的手動重設事件。

## <a name="syntax"></a>語法

```
class event;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[~ event 解構函式](#dtor)|終結事件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[reset](#reset)|事件重設為未收到信號狀態。|
|[set](#set)|通知事件。|
|[wait](#wait)|等候事件變成收到訊號。|
|[wait_for_multiple](#wait_for_multiple)|等候變成已收到訊號的多個事件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|值，表示等候應該永遠不會逾時。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`event`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> 事件

建構新的事件。

```
_CRTIMP event();
```

### <a name="remarks"></a>備註

##  <a name="dtor"></a> ~ 事件

終結事件。

```
~event();
```

### <a name="remarks"></a>備註

應該沒有執行緒在等候事件解構函式執行時。 允許事件解構仍在等候的執行緒，會導致未定義的行為發生。

##  <a name="reset"></a> 重設

事件重設為未收到信號狀態。

```
void reset();
```

##  <a name="set"></a> 設定

通知事件。

```
void set();
```

### <a name="remarks"></a>備註

發出事件訊號會使事件上正在等候的任意數目內容變為可執行。

##  <a name="timeout_infinite"></a> timeout_infinite

值，表示等候應該永遠不會逾時。

```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

##  <a name="wait"></a> 等候

等候事件變成收到訊號。

```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_Timeout*<br/>
等候逾時之前，請指出毫秒的數。值`COOPERATIVE_TIMEOUT_INFINITE`表示沒有逾時。

### <a name="return-value"></a>傳回值

如果滿意等待結果，該值`0`傳回; 否則即為值`COOPERATIVE_WAIT_TIMEOUT`表示等候逾時沒有變成發出信號的事件。

> [!IMPORTANT]
>  在通用 Windows 平台 (UWP) 應用程式中，請勿呼叫`wait`在 ASTA 執行緒上因為這個呼叫可以封鎖目前的執行緒，而且可能會導致應用程式變成沒有回應。

##  <a name="wait_for_multiple"></a> wait_for_multiple

等候變成已收到訊號的多個事件。

```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*_PPEvents*<br/>
要等候的事件陣列。 陣列中的事件數目會由`count`參數。

*count*<br/>
中所提供之陣列中的事件計數的`_PPEvents`參數。

*_FWaitAll*<br/>
如果設定為值 **，則為 true**，參數會指定陣列中的所有事件都提供在`_PPEvents`參數必須變成收到訊號，以滿足等候。 如果設為值**假**，它會指定陣列中的任何事件提供在`_PPEvents`變成收到訊號的參數會滿足等候。

*_Timeout*<br/>
等候逾時之前，請指出毫秒的數。值`COOPERATIVE_TIMEOUT_INFINITE`表示沒有逾時。

### <a name="return-value"></a>傳回值

如果滿意等待結果中, 提供的陣列中的索引`_PPEvents`滿足等候條件; 參數，否則為值`COOPERATIVE_WAIT_TIMEOUT`表示等候逾時沒有所滿足的條件。

### <a name="remarks"></a>備註

如果參數`_FWaitAll`設定為值`true`函式所傳回的索引，表示所有的事件必須以滿足等候變成發出訊號，帶有沒有特殊的意義，不是值的事實以外`COOPERATIVE_WAIT_TIMEOUT`。

> [!IMPORTANT]
> 在通用 Windows 平台 (UWP) 應用程式中，請勿呼叫`wait_for_multiple`在 ASTA 執行緒上因為這個呼叫可以封鎖目前的執行緒，而且可能會導致應用程式變成沒有回應。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
