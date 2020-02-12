---
title: missing_wait 類別
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: cf81d1ee6c144da210da5b1f37aca7910ae37bc8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142381"
---
# <a name="missing_wait-class"></a>missing_wait 類別

這個類別描述 `task_group` 或 `structured_task_group` 物件的建構函式執行時卻仍有工作排程至該物件所擲回的例外狀況。 如果例外狀況導致堆疊回溯而達成解構函式，則永遠不會擲回此例外狀況。

## <a name="syntax"></a>語法

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[missing_wait](#ctor)|已多載。 建構 `missing_wait` 物件。|

## <a name="remarks"></a>備註

不存在的例外狀況流程中，您必須負責呼叫 `task_group` 或 `structured_task_group` 物件的 `wait` 或 `run_and_wait` 方法，然後才允許該物件進行析構。 執行時間會擲回這個例外狀況，表示您忘了呼叫 `wait` 或 `run_and_wait` 方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`missing_wait`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>missing_wait

建構 `missing_wait` 物件。

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[等候](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)
