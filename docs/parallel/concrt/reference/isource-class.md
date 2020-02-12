---
title: ISource 類別
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139310"
---
# <a name="isource-class"></a>ISource 類別

`ISource` 類別是所有來源區塊的介面。 來源區塊會將訊息傳播至 `ITarget` 區塊。

## <a name="syntax"></a>語法

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>參數

*T*<br/>
來源區塊所產生之訊息內裝載的資料類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`source_type`|`T`的類型別名。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[~ ISource 的析構函式](#dtor)|終結 `ISource` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[接受](#accept)|在衍生類別中覆寫時，接受此 `ISource` 區塊所提供的訊息，並將擁有權轉移給呼叫者。|
|[acquire_ref](#acquire_ref)|在衍生類別中覆寫時，取得此 `ISource` 區塊上的參考計數，以防止刪除。|
|[consume](#consume)|在衍生類別中覆寫時，會使用此 `ISource` 區塊先前提供的訊息，並由目標成功保留，並將擁有權轉移給呼叫者。|
|[link_target](#link_target)|在衍生類別中覆寫時，將目標區塊連結至此 `ISource` 區塊。|
|[release](#release)|在衍生類別中覆寫時，釋放前一個成功的訊息保留。|
|[release_ref](#release_ref)|在衍生類別中覆寫時，釋放此 `ISource` 區塊上的參考計數。|
|[reserve](#reserve)|在衍生類別中覆寫時，保留此 `ISource` 區塊先前提供的訊息。|
|[unlink_target](#unlink_target)|在衍生類別中覆寫時，如果發現先前已連結，則會從這個 `ISource` 區塊取消連結目標區塊。|
|[unlink_targets](#unlink_targets)|在衍生類別中覆寫時，取消此 `ISource` 區塊中所有的目標區塊。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`ISource`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="accept"></a>接受

在衍生類別中覆寫時，接受此 `ISource` 區塊所提供的訊息，並將擁有權轉移給呼叫者。

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `accept` 方法之目標區塊的指標。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之訊息的指標。

### <a name="remarks"></a>備註

當此 `ISource` 區塊提供訊息時，目標會呼叫 `accept` 方法。 如果此來源決定要建立訊息的複本，則傳回的訊息指標可能與傳入 `ITarget` 區塊之 `propagate` 方法的不同。

## <a name="acquire_ref"></a>acquire_ref

在衍生類別中覆寫時，取得此 `ISource` 區塊上的參考計數，以防止刪除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由在 `link_target` 方法期間連結至此來源的 `ITarget` 物件所呼叫。

## <a name="consume"></a>占

在衍生類別中覆寫時，會使用此 `ISource` 區塊先前提供的訊息，並由目標成功保留，並將擁有權轉移給呼叫者。

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="dtor"></a>~ ISource

終結 `ISource` 物件。

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

在衍生類別中覆寫時，將目標區塊連結至此 `ISource` 區塊。

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要連結至此 `ISource` 區塊之目標區塊的指標。

## <a name="release"></a>版本

在衍生類別中覆寫時，釋放前一個成功的訊息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
保留 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `release` 方法之目標區塊的指標。

## <a name="release_ref"></a>release_ref

在衍生類別中覆寫時，釋放此 `ISource` 區塊上的參考計數。

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由與此來源取消連結的 `ITarget` 物件所呼叫。 來源區塊可以釋放為目標區塊保留的任何資源。

## <a name="reserve"></a>留成

在衍生類別中覆寫時，保留此 `ISource` 區塊先前提供的訊息。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
所提供 `message` 物件的 `runtime_object_identity`。

*_PTarget*<br/>
呼叫 `reserve` 方法之目標區塊的指標。

### <a name="return-value"></a>傳回值

如果成功保留訊息，**則為 true** ，否則為**false** 。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

在您呼叫 `reserve`之後，如果成功，您必須呼叫 `consume` 或 `release`，以便分別接受或授與訊息的擁有權。

## <a name="unlink_target"></a>unlink_target

在衍生類別中覆寫時，如果發現先前已連結，則會從這個 `ISource` 區塊取消連結目標區塊。

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
從這個 `ISource` 區塊取消連結之目標區塊的指標。

## <a name="unlink_targets"></a>unlink_targets

在衍生類別中覆寫時，取消此 `ISource` 區塊中所有的目標區塊。

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ITarget 類別](itarget-class.md)
