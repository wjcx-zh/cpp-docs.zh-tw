---
title: nested_scheduler_missing_detach 類別
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: 8c9553b036890c4ce28f1060bfe2f58ee1904935
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138860"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach 類別

這個類別描述當並行執行階段偵測到您忘了使用 `CurrentScheduler::Detach` 物件的 `Attach` 方法在附加到第二個排程器上呼叫 `Scheduler` 方法時擲出的例外狀況。

## <a name="syntax"></a>語法

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|已多載。 建構 `nested_scheduler_missing_detach` 物件。|

## <a name="remarks"></a>備註

當您在已由其他排程器擁有或附加的內容上呼叫 `Attach` 物件的`Scheduler` 方法，將排程器巢狀排列在另一個排程器內時，才會擲回這個例外狀況。 當並行執行階段會在偵測到案例以協助找出問題時，擲回此例外狀況都伺機。 並非每個無法呼叫 `CurrentScheduler::Detach` 方法的實例都一定會擲回這個例外狀況。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>nested_scheduler_missing_detach

建構 `nested_scheduler_missing_detach` 物件。

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
