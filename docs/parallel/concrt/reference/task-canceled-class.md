---
title: task_canceled 類別
ms.date: 11/04/2016
f1_keywords:
- task_canceled
- CONCRT/concurrency::task_canceled
- CONCRT/concurrency::task_canceled::task_canceled
helpviewer_keywords:
- task_canceled class
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
ms.openlocfilehash: caef1c62ff09ffb76f74d4a1453e9d59dcb7d45b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385241"
---
# <a name="taskcanceled-class"></a>task_canceled 類別

這個類別描述 PPL 工作分層為了強制目前工作取消，而擲回的例外狀況。 它也會藉由擲回`get()`方法[工作](/visualstudio/extensibility/debugger/task-class-internal-members)，已取消的工作。

## <a name="syntax"></a>語法

```
class task_canceled : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_canceled](#ctor)|多載。 建構 `task_canceled` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`task_canceled`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> task_canceled

建構 `task_canceled` 物件。

```
explicit _CRTIMP task_canceled(_In_z_ const char* _Message) throw();

task_canceled() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
