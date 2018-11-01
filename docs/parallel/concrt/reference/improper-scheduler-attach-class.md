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
ms.openlocfilehash: 617c71115b8a1354dbb1d9998791564f0a5d18de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614704"
---
# <a name="improperschedulerattach-class"></a>improper_scheduler_attach 類別

這個類別描述當 `Scheduler` 物件已經附加到目前的內容上時呼叫 `Attach` 方法擲回的例外狀況。

## <a name="syntax"></a>語法

```
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|多載。 建構 `improper_scheduler_attach` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> improper_scheduler_attach

建構 `improper_scheduler_attach` 物件。

```
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>參數

*訊息 （_m)*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
