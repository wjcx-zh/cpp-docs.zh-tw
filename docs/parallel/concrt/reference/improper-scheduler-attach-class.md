---
title: improper_scheduler_attach 類別
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
ms.openlocfilehash: 85adf3f919d94a82f5a68a5cd9e5f44cdca10006
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141233"
---
# <a name="improper_scheduler_attach-class"></a>improper_scheduler_attach 類別

這個類別描述當 `Attach` 物件已經附加到目前的內容上時呼叫 `Scheduler` 方法擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|已多載。 建構 `improper_scheduler_attach` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>improper_scheduler_attach

建構 `improper_scheduler_attach` 物件。

```cpp
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
