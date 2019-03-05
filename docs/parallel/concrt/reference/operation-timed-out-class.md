---
title: operation_timed_out 類別
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 2511be4669bc4abf75d5188e3aeabd7863f42dd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276100"
---
# <a name="operationtimedout-class"></a>operation_timed_out 類別

這個類別描述作業逾時擲回的例外狀況。

## <a name="syntax"></a>語法

```
class operation_timed_out : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[operation_timed_out](#ctor)|多載。 建構 `operation_timed_out` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`operation_timed_out`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> operation_timed_out

建構 `operation_timed_out` 物件。

```
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
