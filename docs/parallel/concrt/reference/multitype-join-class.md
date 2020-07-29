---
title: multitype_join 類別
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: c648e77e404cf39eab281a93e03d8b427da375f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205856"
---
# <a name="multitype_join-class"></a>multitype_join 類別

`multitype_join` 傳訊區塊是多來源的單一目標傳訊區塊，會與來自其來源的不同類型訊息合併，並且為其目標提供 Tuple 合併的訊息。

## <a name="syntax"></a>語法

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>參數

*T*<br/>
`tuple`區塊所聯結和傳播之訊息的裝載類型。

*_Jtype*<br/>
這種類型的 `join` 區塊為，也就是 `greedy` 或`non_greedy`

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`type`|的類型別名 `T` 。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[multitype_join](#ctor)|已多載。 建構 `multitype_join` 傳訊區塊。|
|[~ multitype_join 的析構函式](#dtor)|損毀 `multitype_join` 訊息區塊。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[接受](#accept)|接受此區塊所提供的訊息 `multitype_join` ，並將擁有權轉移給呼叫者。|
|[acquire_ref](#acquire_ref)|取得此訊息區塊上的參考計數 `multitype_join` ，以防止刪除。|
|[占](#consume)|取用訊息區塊先前提供的訊息 `multitype_join` ，並由目標成功保留，並將擁有權轉移給呼叫者。|
|[link_target](#link_target)|將目標區塊連結至此 `multitype_join` 訊息區塊。|
|[版本](#release)|釋放先前成功的訊息保留。|
|[release_ref](#release_ref)|釋放此訊息區塊上的參考計數 `multiple_join` 。|
|[留成](#reserve)|保留此訊息區塊先前提供的訊息 `multitype_join` 。|
|[unlink_target](#unlink_target)|從這個訊息區塊取消與目標區塊的 `multitype_join` 通訊。|
|[unlink_targets](#unlink_targets)|取消此訊息區塊中所有目標的的 `multitype_join` 通訊。 （覆寫[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="accept"></a><a name="accept"></a>接受

接受此區塊所提供的訊息 `multitype_join` ，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `accept` 。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之訊息的指標。

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

取得此訊息區塊上的參考計數 `multitype_join` ，以防止刪除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由在 `ITarget` 方法期間連結至此來源的物件所呼叫 `link_target` 。

## <a name="consume"></a><a name="consume"></a>占

取用訊息區塊先前提供的訊息 `multitype_join` ，並由目標成功保留，並將擁有權轉移給呼叫者。

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `consume` 。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其 `message` 擁有權之物件的指標。

### <a name="remarks"></a>備註

`consume`方法與類似 `accept` ，但一定會在傳回的呼叫前面加上 `reserve` **`true`** 。

## <a name="link_target"></a><a name="link_target"></a>link_target

將目標區塊連結至此 `multitype_join` 訊息區塊。

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要 `ITarget` 連結至此訊息區塊之區塊的指標 `multitype_join` 。

## <a name="multitype_join"></a><a name="ctor"></a>multitype_join

建構 `multitype_join` 傳訊區塊。

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>參數

*_Tuple*<br/>
此 `tuple` 傳訊區塊的 `multitype_join` 來源。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

*_Join*<br/>
作為複製來源處的 `multitype_join` 傳訊區塊。 請注意，原始物件會被遺棄，使其成為移動建構函式。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

移動建構函式不會在鎖定下執行，這表示使用者必須確認在移動時沒有任何輕量工作在執行中。 否則，可能發生許多競爭情況，導致例外狀況或不一致的狀態。

## <a name="multitype_join"></a><a name="dtor"></a>~ multitype_join

損毀 `multitype_join` 訊息區塊。

```cpp
~multitype_join();
```

## <a name="release"></a><a name="release"></a>版本

釋放先前成功的訊息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 正在釋放之物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `release` 。

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

釋放此訊息區塊上的參考計數 `multiple_join` 。

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由與 `ITarget` 此來源取消連結的物件所呼叫。 來源區塊可以釋放為目標區塊保留的任何資源。

## <a name="reserve"></a><a name="reserve"></a>留成

保留此訊息區塊先前提供的訊息 `multitype_join` 。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity` `message` 要保留之物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `reserve` 。

### <a name="return-value"></a>傳回值

**`true`** 如果訊息已成功保留，則 **`false`** 為，否則為。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

在您呼叫之後， `reserve` 如果成功，您必須呼叫 `consume` 或， `release` 以便分別接受或放棄訊息。

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

從這個訊息區塊取消與目標區塊的 `multitype_join` 通訊。

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要與 `ITarget` 此訊息區塊取消連結之區塊的指標 `multitype_join` 。

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

取消此訊息區塊中所有目標的的 `multitype_join` 通訊。

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[choice 類別](choice-class.md)<br/>
[join 類別](join-class.md)
