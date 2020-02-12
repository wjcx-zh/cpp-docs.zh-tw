---
title: invalid_oversubscribe_operation 類別
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 7a879fc2da2f963cd4b5ea5fcd7e9506f86ce051
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140839"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation 類別

這個類別描述當呼叫 `Context::Oversubscribe` 方法時，如果 `_BeginOversubscription` 參數設定為**false** ，而沒有先前呼叫 `Context::Oversubscribe` 方法，並將 `_BeginOversubscription` 參數設為**true**，則擲回例外狀況。

## <a name="syntax"></a>語法

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|已多載。 建構 `invalid_oversubscribe_operation` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>invalid_oversubscribe_operation

建構 `invalid_oversubscribe_operation` 物件。

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
