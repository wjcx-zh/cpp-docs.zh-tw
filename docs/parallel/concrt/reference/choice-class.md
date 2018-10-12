---
title: choice 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d38b8415b5ca214800c968d186f37c020dce6dc
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163955"
---
# <a name="choice-class"></a>choice 類別

`choice` 傳訊區塊是多來源的單一目標區塊，代表與一組來源的控制流程互動。 選擇區塊會等候多個來源的其中一個來產生訊息，而且會傳播產生訊息之來源的索引。

## <a name="syntax"></a>語法

```
template<
    class T
>
class choice: public ISource<size_t>;
```

#### <a name="parameters"></a>參數

*T*<br/>
A `tuple`-基底類型表示的輸入來源的裝載。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|類型別名`T`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[choice](#ctor)|多載。 建構 `choice` 傳訊區塊。|
|[~ choice 解構函式](#dtor)|終結`choice`傳訊區塊。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[accept](#accept)|接受的訊息，由此`choice`區塊中，將擁有權傳送給呼叫者。|
|[acquire_ref](#acquire_ref)|取得此參考計數`choice`傳訊區塊，以防止刪除。|
|[consume](#consume)|會使用先前由此訊息`choice`傳訊區塊和目標，將擁有權傳送給呼叫者已成功保留。|
|[has_value](#has_value)|檢查是否這`choice`傳訊區塊已使用值尚未初始化。|
|[index](#index)|傳回的索引`tuple`代表所選取的項目`choice`傳訊區塊。|
|[link_target](#link_target)|將目標區塊連結至這個`choice`傳訊區塊。|
|[release](#release)|釋放先前成功的訊息保留。|
|[release_ref](#release_ref)|釋放此參考計數`choice`傳訊區塊。|
|[reserve](#reserve)|保留先前由此訊息`choice`傳訊區塊。|
|[unlink_target](#unlink_target)|取消連結的目標區塊，從這個`choice`傳訊區塊。|
|[unlink_targets](#unlink_targets)|取消連結所有的目標，從這個`choice`傳訊區塊。 (覆寫[isource:: Unlink_targets](isource-class.md#unlink_targets)。)|
|[值](#value)|取得索引的所選取的訊息`choice`傳訊區塊。|

## <a name="remarks"></a>備註

選擇區塊可確保只有其中一個內送訊息會取用。

如需詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>需求

**標頭：** agents.h

**命名空間：** concurrency

##  <a name="accept"></a> 接受

接受的訊息，由此`choice`區塊中，將擁有權傳送給呼叫者。

```
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`提供的`message`物件。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`accept`方法。

### <a name="return-value"></a>傳回值

指標，呼叫者現在擁有的訊息。

##  <a name="acquire_ref"></a> acquire_ref

取得此參考計數`choice`傳訊區塊，以防止刪除。

```
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
正在呼叫這個方法的目標區塊的指標。

### <a name="remarks"></a>備註

這個方法會呼叫`ITarget`物件所要連結到這個來源期間，`link_target`方法。

##  <a name="ctor"></a> 選擇

建構 `choice` 傳訊區塊。

```
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

##  <a name="dtor"></a> ~ 選擇

終結`choice`傳訊區塊。

```
~choice();
```

##  <a name="consume"></a> 使用

會使用先前由此訊息`choice`傳訊區塊和目標，將擁有權傳送給呼叫者已成功保留。

```
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的保留`message`物件。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`consume`方法。

### <a name="return-value"></a>傳回值

指標`message`物件，呼叫者現在會有的擁有權。

### <a name="remarks"></a>備註

`consume`方法是類似`accept`，但必須一律加上呼叫`reserve`傳回**true**。

##  <a name="has_value"></a> has_value

檢查是否這`choice`傳訊區塊已使用值尚未初始化。

```
bool has_value() const;

```

### <a name="return-value"></a>傳回值

**真**區塊已收到的值，如果**false**否則。

##  <a name="index"></a> 索引

傳回的索引`tuple`代表所選取的項目`choice`傳訊區塊。

```
size_t index();
```

### <a name="return-value"></a>傳回值

訊息的索引。

### <a name="remarks"></a>備註

可以使用擷取的訊息承載`get`方法。

##  <a name="link_target"></a> link_target

將目標區塊連結至這個`choice`傳訊區塊。

```
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
指標`ITarget`連結到此區塊`choice`傳訊區塊。

##  <a name="release"></a> 版本

釋放先前成功的訊息保留。

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件被釋放。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`release`方法。

##  <a name="release_ref"></a> release_ref

釋放此參考計數`choice`傳訊區塊。

```
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
正在呼叫這個方法的目標區塊的指標。

### <a name="remarks"></a>備註

這個方法會呼叫`ITarget`要從這個來源取消連結的物件。 來源區塊允許釋放任何資源保留給目標區塊。

##  <a name="reserve"></a> 保留

保留先前由此訊息`choice`傳訊區塊。

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_MsgId*<br/>
`runtime_object_identity`的`message`物件所保留。

*_PTarget*<br/>
正在呼叫的目標區塊的指標`reserve`方法。

### <a name="return-value"></a>傳回值

**真**已成功保留訊息，如果**false**否則。 保留失敗可能有許多原因，包括：訊息已經保留或已由另一個目標接受、來源拒絕保留等等。

### <a name="remarks"></a>備註

在您呼叫後`reserve`，如果成功，您必須呼叫`consume`或`release`以便採取或分別放棄訊息，因此擁有。

##  <a name="unlink_target"></a> unlink_target

取消連結的目標區塊，從這個`choice`傳訊區塊。

```
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>參數

*_PTarget*<br/>
指標`ITarget`若要從這個取消連結的區塊`choice`傳訊區塊。

##  <a name="unlink_targets"></a> unlink_targets

取消連結所有的目標，從這個`choice`傳訊區塊。

```
virtual void unlink_targets();
```

### <a name="remarks"></a>備註

這個方法不需要從解構函式呼叫，因為解構函式適用於內部`single_assignment`區塊將會取消連結正確。

##  <a name="value"></a> 值

取得索引的所選取的訊息`choice`傳訊區塊。

```
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>參數

*_Payload_type*<br/>
訊息裝載的類型。

### <a name="return-value"></a>傳回值

訊息的承載。

### <a name="remarks"></a>備註

因為 `choice` 傳訊區塊可以接受具有不同類型承載的輸入，因此您必須在擷取時指定承載的類型。 您可以決定根據結果的型別`index`方法。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[join 類別](join-class.md)<br/>
[single_assignment 類別](single-assignment-class.md)
