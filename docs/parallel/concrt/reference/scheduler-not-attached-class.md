---
title: scheduler_not_attached 類別
ms.date: 11/04/2016
f1_keywords:
- scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached
- CONCRT/concurrency::scheduler_not_attached::scheduler_not_attached
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
ms.openlocfilehash: a3b1c113e5c6c5feb5b2fa1940ee9b984233e4af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142199"
---
# <a name="scheduler_not_attached-class"></a>scheduler_not_attached 類別

這個類別描述作業需要將排程器附加至目前內容，而卻沒有這麼做時所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class scheduler_not_attached : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scheduler_not_attached](#ctor)|已多載。 建構 `scheduler_not_attached` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`scheduler_not_attached`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>scheduler_not_attached

建構 `scheduler_not_attached` 物件。

```cpp
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)
