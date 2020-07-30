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
ms.openlocfilehash: 0c95d234fee412c1dacb014dd135ca56fc73bf5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193961"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation 類別

這個類別描述當呼叫方法時所擲回的例外狀況， `Context::Oversubscribe` 其中 `_BeginOversubscription` 參數設定為， **`false`** 而不需要先前呼叫 `Context::Oversubscribe` 方法，並將 `_BeginOversubscription` 參數設定為 **`true`** 。

## <a name="syntax"></a>語法

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|已多載。 建構 `invalid_oversubscribe_operation` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** 並行

## <a name="invalid_oversubscribe_operation"></a><a name="ctor"></a>invalid_oversubscribe_operation

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
