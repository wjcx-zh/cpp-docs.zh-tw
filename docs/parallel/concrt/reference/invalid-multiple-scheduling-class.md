---
title: invalid_multiple_scheduling 類別
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: a8b2a045ce94562dcba0019bc03aaa90c4d384a9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140896"
---
# <a name="invalid_multiple_scheduling-class"></a>invalid_multiple_scheduling 類別

這個類別描述使用 `task_handle` 或 `run` 物件的 `task_group` 方法多次排程 `structured_task_group` 物件，而不中間變更呼叫 `wait` 或 `run_and_wait` 方法時擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|已多載。 建構 `invalid_multiple_scheduling` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>invalid_multiple_scheduling

建構 `invalid_multiple_scheduling` 物件。

```cpp
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_handle 類別](task-handle-class.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[run](task-group-class.md)<br/>
[等候](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)
