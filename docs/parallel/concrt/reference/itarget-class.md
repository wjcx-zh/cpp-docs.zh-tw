---
title: ITarget 類別
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: 39aebd9d82f098225c1275ac6f43d64fc1ce3ba8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231711"
---
# <a name="itarget-class"></a>ITarget 類別

`ITarget` 類別是所有目標區塊的介面。 目標區塊會使用 `ISource` 區塊提供給它們的訊息。

## <a name="syntax"></a>語法

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>參數

*T*<br/>
目標區塊所接受之訊息內裝載的資料類型。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`filter_method`|區塊所使用之任何方法的簽章，會傳回 **`bool`** 值以判斷是否應該接受所提供的訊息。|
|`type`|的類型別名 `T` 。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[~ ITarget 的析構函式](#dtor)|終結 `ITarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[傳遞](#propagate)|在衍生類別中覆寫時，以非同步方式將訊息從來源區塊傳遞至此目標區塊。|
|[send](#send)|在衍生類別中覆寫時，以同步方式將訊息傳遞至目標區塊。|
|[supports_anonymous_source](#supports_anonymous_source)|在衍生類別中覆寫時，會根據訊息區塊是否會接受未與它連結的來源所提供的訊息傳回 true 或 false。 如果覆寫的方法傳回 **`true`** ，目標就無法延後所提供的訊息，因為在稍後使用延遲的訊息時，需要在其來源連結登錄中識別來源。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[link_source](#link_source)|在衍生類別中覆寫時，將指定的來源區塊連結至這個 `ITarget` 區塊。|
|[unlink_source](#unlink_source)|在衍生類別中覆寫時，從這個區塊取消與指定的來源區塊的的 `ITarget` 。|
|[unlink_sources](#unlink_sources)|在衍生類別中覆寫時，取消此區塊中的所有來源區塊 `ITarget` 。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ITarget`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** 並行

## <a name="itarget"></a><a name="dtor"></a>~ ITarget

終結 `ITarget` 物件。

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a><a name="link_source"></a>link_source

在衍生類別中覆寫時，將指定的來源區塊連結至這個 `ITarget` 區塊。

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PSource*<br/>
`ISource`要連結到此區塊的區塊 `ITarget` 。

### <a name="remarks"></a>備註

此函式不應直接在區塊上呼叫 `ITarget` 。 區塊應該使用 `link_target` 方法在區塊上連接在一起 `ISource` ，這會 `link_source` 在對應的目標上叫用方法。

## <a name="propagate"></a><a name="propagate"></a>傳遞

在衍生類別中覆寫時，以非同步方式將訊息從來源區塊傳遞至此目標區塊。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

### <a name="remarks"></a>備註

如果[invalid_argument](../../../standard-library/invalid-argument-class.md) `_PMessage` 或 `_PSource` 參數為，則方法會擲回 invalid_argument 例外狀況 `NULL` 。

## <a name="send"></a><a name="send"></a>發送

在衍生類別中覆寫時，以同步方式將訊息傳遞至目標區塊。

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PMessage*<br/>
`message` 物件的指標。

*_PSource*<br/>
提供訊息之來源區塊的指標。

### <a name="return-value"></a>傳回值

[Message_status](concurrency-namespace-enums.md)指出目標決定要如何處理訊息。

### <a name="remarks"></a>備註

如果[invalid_argument](../../../standard-library/invalid-argument-class.md) `_PMessage` 或 `_PSource` 參數為，則方法會擲回 invalid_argument 例外狀況 `NULL` 。

在 `send` 訊息起始之外使用方法，並在網路內傳播訊息是危險的，而且可能會導致鎖死。

當 `send` 傳回時，訊息可能已經被接受，並已傳送到目標區塊，或已被目標拒絕。

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

在衍生類別中覆寫時，會根據訊息區塊是否會接受未與它連結的來源所提供的訊息傳回 true 或 false。 如果覆寫的方法傳回 **`true`** ，目標就無法延後所提供的訊息，因為在稍後使用延遲的訊息時，需要在其來源連結登錄中識別來源。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

**`true`** 如果區塊可以接受未與它連結之來源的訊息，則為， **`false`** 否則為。

## <a name="unlink_source"></a><a name="unlink_source"></a>unlink_source

在衍生類別中覆寫時，從這個區塊取消與指定的來源區塊的的 `ITarget` 。

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PSource*<br/>
`ISource`正在從這個區塊取消連結的區塊 `ITarget` 。

### <a name="remarks"></a>備註

此函式不應直接在區塊上呼叫 `ITarget` 。 區塊應使用 `unlink_target` 或 `unlink_targets` 方法在區塊上中斷連接 `ISource` ，這會在 `unlink_source` 對應的目標上叫用方法。

## <a name="unlink_sources"></a><a name="unlink_sources"></a>unlink_sources

在衍生類別中覆寫時，取消此區塊中的所有來源區塊 `ITarget` 。

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ISource 類別](isource-class.md)
