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
ms.openlocfilehash: 121e61447775cdcb5d7f5f1187c5d4cc6b7d68b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265648"
---
# <a name="improperschedulerreference-class"></a>improper_scheduler_reference 類別

這個類別描述在被關閉的 `Scheduler` 物件 (來自不屬於排程器的內容) 上呼叫 `Reference` 方法所擲回的例外狀況。

## <a name="syntax"></a>語法

```
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|多載。 建構 `improper_scheduler_reference` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> improper_scheduler_reference

建構 `improper_scheduler_reference` 物件。

```
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
