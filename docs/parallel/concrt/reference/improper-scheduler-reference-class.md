---
title: improper_scheduler_reference 類別
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 18536043b0d46a6f27f1e5c60778a22af82ad2d3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141104"
---
# <a name="improper_scheduler_reference-class"></a>improper_scheduler_reference 類別

這個類別描述在被關閉的 `Reference` 物件 (來自不屬於排程器的內容) 上呼叫 `Scheduler` 方法所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|已多載。 建構 `improper_scheduler_reference` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>improper_scheduler_reference

建構 `improper_scheduler_reference` 物件。

```cpp
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
