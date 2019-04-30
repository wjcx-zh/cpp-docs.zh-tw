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
ms.openlocfilehash: 68d24d710eec4fd602e64cc3cbde810db2b1a495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409963"
---
# <a name="missingwait-class"></a>missing_wait 類別

這個類別描述 `task_group` 或 `structured_task_group` 物件的建構函式執行時卻仍有工作排程至該物件所擲回的例外狀況。 如果例外狀況導致堆疊回溯而達成解構函式，則永遠不會擲回此例外狀況。

## <a name="syntax"></a>語法

```
class missing_wait : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[missing_wait](#ctor)|多載。 建構 `missing_wait` 物件。|

## <a name="remarks"></a>備註

不存在的例外狀況流程，您必須負責呼叫`wait`或是`run_and_wait`方法`task_group`或`structured_task_group`之前允許解構該物件的物件。 執行階段會擲回這個例外狀況，您忘了呼叫來指出`wait`或`run_and_wait`方法。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`missing_wait`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> missing_wait

建構 `missing_wait` 物件。

```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[task_group 類別](task-group-class.md)<br/>
[wait](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group 類別](structured-task-group-class.md)
