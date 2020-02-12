---
title: context_unblock_unbalanced 類別
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143101"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced 類別

這個類別描述未正確配對 `Context` 物件的 `Block` 和 `Unblock` 方法的呼叫時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[coNtext_unblock_unbalanced](#ctor)|已多載。 建構 `context_unblock_unbalanced` 物件。|

## <a name="remarks"></a>備註

對 `Context` 物件的 `Block` 和 `Unblock` 方法的呼叫必須一律正確配對。 並行執行階段允許以任一順序發生作業。 例如，呼叫 `Block` 之後可以呼叫 `Unblock`，反之亦然。 例如，如果在一個資料列中，對未封鎖的 `Context` 物件呼叫了兩個 `Unblock` 方法，就會擲回這個例外狀況。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>coNtext_unblock_unbalanced

建構 `context_unblock_unbalanced` 物件。

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
