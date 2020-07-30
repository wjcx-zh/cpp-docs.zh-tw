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
ms.openlocfilehash: df592e965b436ed5a1d60702f9e57088887d5a94
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222702"
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

|名稱|說明|
|----------|-----------------|
|`source_type`|的類型別名 `T` 。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[~ ISource 的析構函式](#dtor)|終結 `ISource` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[接受](#accept)|在衍生類別中覆寫時，接受此區塊所提供的訊息 `ISource` ，並將擁有權轉移給呼叫者。|
|[acquire_ref](#acquire_ref)|在衍生類別中覆寫時，取得此區塊上的參考計數 `ISource` ，以防止刪除。|
|[占](#consume)|在衍生類別中覆寫時，會使用此區塊先前提供的訊息， `ISource` 並由目標成功保留，並將擁有權轉移給呼叫者。|
|[link_target](#link_target)|在衍生類別中覆寫時，將目標區塊連結至這個 `ISource` 區塊。|
|[版本](#release)|在衍生類別中覆寫時，釋放前一個成功的訊息保留。|
|[release_ref](#release_ref)|在衍生類別中覆寫時，釋放此區塊上的參考計數 `ISource` 。|
|[留成](#reserve)|在衍生類別中覆寫時，保留此區塊先前提供的訊息 `ISource` 。|
|[unlink_target](#unlink_target)|在衍生類別中覆寫時，如果發現先前已連結，則從這個區塊取消連結目標區塊 `ISource` 。|
|[unlink_targets](#unlink_targets)|在衍生類別中覆寫時，取消此區塊中所有的目標區塊 `ISource` 。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ISource`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="accept"></a><a name="accept"></a>接受

在衍生類別中覆寫時，接受此區塊所提供的訊息 `ISource` ，並將擁有權轉移給呼叫者。

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `accept` 。

### <a name="return-value"></a>傳回值

呼叫端目前擁有其擁有權之訊息的指標。

### <a name="remarks"></a>備註

`accept`當此區塊提供訊息時，目標會呼叫方法 `ISource` 。 `propagate` `ITarget` 如果此來源決定要建立訊息的複本，則傳回的訊息指標可能會與傳入區塊之方法的不同。

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

在衍生類別中覆寫時，取得此區塊上的參考計數 `ISource` ，以防止刪除。

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由在 `ITarget` 方法期間連結至此來源的物件所呼叫 `link_target` 。

## <a name="consume"></a><a name="consume"></a>占

在衍生類別中覆寫時，會使用此區塊先前提供的訊息， `ISource` 並由目標成功保留，並將擁有權轉移給呼叫者。

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="isource"></a><a name="dtor"></a>~ ISource

終結 `ISource` 物件。

```cpp
virtual ~ISource();
```

## <a name="link_target"></a><a name="link_target"></a>link_target

在衍生類別中覆寫時，將目標區塊連結至這個 `ISource` 區塊。

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
要連結至此區塊之目標區塊的指標 `ISource` 。

## <a name="release"></a><a name="release"></a>版本

在衍生類別中覆寫時，釋放前一個成功的訊息保留。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`保留 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `release` 。

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

在衍生類別中覆寫時，釋放此區塊上的參考計數 `ISource` 。

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
呼叫這個方法之目標區塊的指標。

### <a name="remarks"></a>備註

這個方法是由與 `ITarget` 此來源取消連結的物件所呼叫。 來源區塊可以釋放為目標區塊保留的任何資源。

## <a name="reserve"></a><a name="reserve"></a>留成

在衍生類別中覆寫時，保留此區塊先前提供的訊息 `ISource` 。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`所提供之 `message` 物件的。

*_PTarget*<br/>
呼叫方法之目標區塊的指標 `reserve` 。

### <a name="return-value"></a>傳回值

**`true`** 如果訊息已成功保留，則 **`false`** 為，否則為。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

在您呼叫之後， `reserve` 如果成功，您必須呼叫 `consume` 或， `release` 以便分別接受或放棄訊息。

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

在衍生類別中覆寫時，如果發現先前已連結，則從這個區塊取消連結目標區塊 `ISource` 。

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
從這個區塊取消連結之目標區塊的指標 `ISource` 。

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

在衍生類別中覆寫時，取消此區塊中所有的目標區塊 `ISource` 。

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ITarget 類別](itarget-class.md)
