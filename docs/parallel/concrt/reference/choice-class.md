---
title: choice 類別
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142221"
---
# <a name="choice-class"></a>choice 類別

`choice` 傳訊區塊是多來源的單一目標區塊，代表與一組來源的控制流程互動。 選擇區塊會等候多個來源的其中一個來產生訊息，而且會傳播產生訊息之來源的索引。

## <a name="syntax"></a>語法

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>參數

*T*<br/>
以 `tuple`為基礎的類型，代表輸入來源的裝載。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|`T`的類型別名。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[選擇](#ctor)|已多載。 建構 `choice` 傳訊區塊。|
|[~ 選擇函式](#dtor)|損毀 `choice` 訊息區塊。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[接受](#accept)|接受此 `choice` 封鎖所提供的訊息，並將擁有權轉移給呼叫者。|
|[acquire_ref](#acquire_ref)|取得此 `choice` 訊息區塊上的參考計數，以防止刪除。|
|[consume](#consume)|使用此 `choice` 訊息區塊先前提供的訊息，並已由目標成功保留，並將擁有權轉移給呼叫者。|
|[has_value](#has_value)|檢查此 `choice` 訊息區塊是否已使用值進行初始化。|
|[index](#index)|將索引傳回 `tuple`，代表 `choice` 訊息區塊所選取的元素。|
|[link_target](#link_target)|將目標區塊連結至此 `choice` 訊息區塊。|
|[release](#release)|釋放先前成功的訊息保留。|
|[release_ref](#release_ref)|釋放此 `choice` 訊息區塊上的參考計數。|
|[reserve](#reserve)|保留此 `choice` 訊息區塊先前提供的訊息。|
|[unlink_target](#unlink_target)|從這個 `choice` 的訊息區塊取消與目標區塊的的通訊。|
|[unlink_targets](#unlink_targets)|取消此 `choice` 訊息區塊中所有目標的的通訊。 （覆寫[ISource：： unlink_targets](isource-class.md#unlink_targets)。）|
|[value](#value)|取得 `choice` 訊息區塊已選取其索引的訊息。|

## <a name="remarks"></a>備註

選擇區塊可確保只會使用其中一個傳入訊息。

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="accept"></a>接受

接受此 `choice` 封鎖所提供的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `accept` 方法之目標區塊的指標。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之訊息的指標。

## <a name="acquire_ref"></a>acquire_ref

取得此 `choice` 訊息區塊上的參考計數，以防止刪除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由在 `link_target` 方法期間連結至此來源的 `ITarget` 物件所呼叫。

## <a name="ctor"></a>選擇

建構 `choice` 傳訊區塊。

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>參數

*_Tuple*<br/>
選擇的 `tuple` 來源。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

*_Choice*<br/>
作為複製來源處的 `choice` 傳訊區塊。 請注意，原始物件會被遺棄，使其成為移動建構函式。

### <a name="remarks"></a>備註

如果您未指定 `_PScheduler` 或 `_PScheduleGroup` 參數，執行階段會使用預設排程器。

移動建構函式不會在鎖定下執行，這表示使用者必須確認在移動時沒有任何輕量工作在執行中。 否則，可能發生許多競爭情況，導致例外狀況或不一致的狀態。

## <a name="dtor"></a>~ 選擇

損毀 `choice` 訊息區塊。

```cpp
~choice();
```

## <a name="consume"></a>占

使用此 `choice` 訊息區塊先前提供的訊息，並已由目標成功保留，並將擁有權轉移給呼叫者。

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
保留 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `consume` 方法之目標區塊的指標。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之 `message` 物件的指標。

### <a name="remarks"></a>備註

`consume` 方法與 `accept`類似，但前面必須加上傳回**true**之 `reserve` 的呼叫。

## <a name="has_value"></a>has_value

檢查此 `choice` 訊息區塊是否已使用值進行初始化。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>傳回值

如果區塊已收到值，**則為 true** ，否則為**false** 。

## <a name="index"></a>指數

將索引傳回 `tuple`，代表 `choice` 訊息區塊所選取的元素。

```cpp
size_t index();
```

### <a name="return-value"></a>傳回值

訊息索引。

### <a name="remarks"></a>備註

您可以使用 `get` 方法來解壓縮訊息承載。

## <a name="link_target"></a>link_target

將目標區塊連結至此 `choice` 訊息區塊。

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要連結至此 `choice` 訊息區塊之 `ITarget` 區塊的指標。

## <a name="release"></a>版本

釋放先前成功的訊息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
要釋放之 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `release` 方法之目標區塊的指標。

## <a name="release_ref"></a>release_ref

釋放此 `choice` 訊息區塊上的參考計數。

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由與此來源取消連結的 `ITarget` 物件所呼叫。 來源區塊可以釋放為目標區塊保留的任何資源。

## <a name="reserve"></a>留成

保留此 `choice` 訊息區塊先前提供的訊息。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
要保留之 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `reserve` 方法之目標區塊的指標。

### <a name="return-value"></a>傳回值

如果成功保留訊息，**則為 true** ，否則為**false** 。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

在您呼叫 `reserve`之後，如果成功，您必須呼叫 `consume` 或 `release`，以便分別接受或授與訊息的擁有權。

## <a name="unlink_target"></a>unlink_target

從這個 `choice` 的訊息區塊取消與目標區塊的的通訊。

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要與此 `choice` 訊息區塊取消連結之 `ITarget` 區塊的指標。

## <a name="unlink_targets"></a>unlink_targets

取消此 `choice` 訊息區塊中所有目標的的通訊。

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>備註

不需要從析構函式呼叫這個方法，因為內部 `single_assignment` 區塊的析構函式會適當地取消連結。

## <a name="value"></a>value

取得 `choice` 訊息區塊已選取其索引的訊息。

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>參數

*_Payload_type*<br/>
訊息裝載的類型。

### <a name="return-value"></a>傳回值

訊息的裝載。

### <a name="remarks"></a>備註

因為 `choice` 傳訊區塊可以接受具有不同類型承載的輸入，因此您必須在擷取時指定承載的類型。 您可以根據 `index` 方法的結果來判斷型別。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[join 類別](join-class.md)<br/>
[single_assignment 類別](single-assignment-class.md)
