---
title: invalid_scheduler_policy_thread_specification 類別
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: 26d09610c6bb9e0c87852c9804e094617b021273
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341092"
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification 類別

這個類別描述嘗試設定 `SchedulerPolicy` 物件的並行存取限制，以致 `MinConcurrency` 機碼的值小於 `MaxConcurrency` 機碼的值時擲回的例外狀況。

## <a name="syntax"></a>語法

```
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|多載。 建構 `invalid_scheduler_policy_value` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency
##  <a name="ctor"></a> invalid_scheduler_policy_thread_specification

建構 `invalid_scheduler_policy_value` 物件。

```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[SchedulerPolicy 類別](schedulerpolicy-class.md)
