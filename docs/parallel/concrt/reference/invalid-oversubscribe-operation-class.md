---
title: invalid_oversubscribe_operation 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1728053c7b42afedb4cda9b2dc96a089750a866
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161693"
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

*訊息 （_m)*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
