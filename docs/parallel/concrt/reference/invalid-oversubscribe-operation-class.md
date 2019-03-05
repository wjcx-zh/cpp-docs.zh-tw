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
ms.openlocfilehash: 200743d41c1c45f2a957dba0716dd7aa07e3de76
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266675"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation 類別

這個類別描述時所擲回的例外狀況`Context::Oversubscribe`方法呼叫`_BeginOversubscription`參數設為**false**卻沒有先前呼叫`Context::Oversubscribe`方法`_BeginOversubscription`參數設定為 **，則為 true**。

## <a name="syntax"></a>語法

```
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|多載。 建構 `invalid_oversubscribe_operation` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> invalid_oversubscribe_operation

建構 `invalid_oversubscribe_operation` 物件。

```
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
