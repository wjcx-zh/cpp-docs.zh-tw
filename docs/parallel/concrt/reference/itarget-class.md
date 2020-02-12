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
ms.openlocfilehash: dc9eacad744536e640417a4ebf51b975bd05bcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142039"
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

|名稱|描述|
|----------|-----------------|
|`filter_method`|區塊所使用之任何方法的簽章，會傳回 `bool` 值，以判斷是否應該接受所提供的訊息。|
|`type`|`T`的類型別名。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[~ ITarget 的析構函式](#dtor)|終結 `ITarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[傳遞](#propagate)|在衍生類別中覆寫時，以非同步方式將訊息從來源區塊傳遞至此目標區塊。|
|[傳送](#send)|在衍生類別中覆寫時，以同步方式將訊息傳遞至目標區塊。|
|[supports_anonymous_source](#supports_anonymous_source)|在衍生類別中覆寫時，會根據訊息區塊是否會接受未與它連結的來源所提供的訊息傳回 true 或 false。 如果覆寫的方法傳回**true**，則目標無法延後提供的訊息，因為在稍後使用延遲的訊息時，需要在其來源連結登錄中識別來源。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[link_source](#link_source)|在衍生類別中覆寫時，將指定的來源區塊連結至此 `ITarget` 區塊。|
|[unlink_source](#unlink_source)|在衍生類別中覆寫時，從這個 `ITarget` 區塊取消與指定的來源區塊的的。|
|[unlink_sources](#unlink_sources)|在衍生類別中覆寫時，取消此 `ITarget` 區塊中的所有來源區塊。|

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[非同步訊息區塊](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`ITarget`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

## <a name="dtor"></a>~ ITarget

終結 `ITarget` 物件。

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a>link_source

在衍生類別中覆寫時，將指定的來源區塊連結至此 `ITarget` 區塊。

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PSource*<br/>
要連結到這個 `ITarget` 區塊的 `ISource` 區塊。

### <a name="remarks"></a>備註

此函式不應直接在 `ITarget` 區塊上呼叫。 區塊應該使用 `ISource` 區塊上的 `link_target` 方法連接在一起，這會在對應的目標上叫用 `link_source` 方法。

## <a name="propagate"></a>傳遞

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

如果 `_PMessage` 或 `_PSource` 參數 `NULL`，方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

## <a name="send"></a>發送

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

如果 `_PMessage` 或 `_PSource` 參數 `NULL`，方法會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況。

在訊息初始外使用 `send` 方法，並在網路內傳播訊息是危險的，而且可能會導致鎖死。

當 `send` 傳回時，訊息可能已經被接受，並已傳送到目標區塊，或已被目標拒絕。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

在衍生類別中覆寫時，會根據訊息區塊是否會接受未與它連結的來源所提供的訊息傳回 true 或 false。 如果覆寫的方法傳回**true**，則目標無法延後提供的訊息，因為稍後延遲的訊息耗用量需要在其來源連結登錄中識別來源。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>傳回值

如果區塊可以接受未連結至來源的訊息，**則為 true** ，否則為**false** 。

## <a name="unlink_source"></a>unlink_source

在衍生類別中覆寫時，從這個 `ITarget` 區塊取消與指定的來源區塊的的。

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>參數

*_PSource*<br/>
正在從這個 `ITarget` 區塊取消連結 `ISource` 區塊。

### <a name="remarks"></a>備註

此函式不應直接在 `ITarget` 區塊上呼叫。 區塊應該使用 `unlink_target` 或 `unlink_targets` 方法在 `ISource` 區塊上中斷連接，這會在對應的目標上叫用 `unlink_source` 方法。

## <a name="unlink_sources"></a>unlink_sources

在衍生類別中覆寫時，取消此 `ITarget` 區塊中的所有來源區塊。

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ISource 類別](isource-class.md)
