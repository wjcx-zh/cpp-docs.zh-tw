---
title: invalid_scheduler_policy_key 類別
ms.date: 11/04/2016
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
ms.openlocfilehash: 60d5a57ff9cb33a3d522c14514f5107844216852
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143017"
---
# <a name="invalid_scheduler_policy_key-class"></a>invalid_scheduler_policy_key 類別

這個類別描述將無效或未知的機碼傳遞給 `SchedulerPolicy` 物件建構函式，或將必須使用其他方式 (如 `SetPolicyValue` 方法) 變更的機碼傳遞給 `SchedulerPolicy` 物件的 `SetConcurrencyLimits` 方法時所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|已多載。 建構 `invalid_scheduler_policy_key` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>invalid_scheduler_policy_key

建構 `invalid_scheduler_policy_key` 物件。

```cpp
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[SchedulerPolicy 類別](schedulerpolicy-class.md)
