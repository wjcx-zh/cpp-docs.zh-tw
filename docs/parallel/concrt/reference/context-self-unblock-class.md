---
title: context_self_unblock 類別
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 900dc68eac4441bd1db3818d3c1f30698b80a6e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296172"
---
# <a name="contextselfunblock-class"></a>context_self_unblock 類別

這個類別描述從同樣的內容呼叫 `Context` 物件的 `Unblock` 方法所擲回的例外狀況。 這會指出指定內容自行解除封鎖的嘗試。

## <a name="syntax"></a>語法

```
class context_self_unblock : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[context_self_unblock](#ctor)|多載。 建構 `context_self_unblock` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`context_self_unblock`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> context_self_unblock

建構 `context_self_unblock` 物件。

```
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
