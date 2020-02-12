---
title: uninitialized_object 類別
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: ef7ded0bf925d3430b70064c4979b75e08f9cf45
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127695"
---
# <a name="uninitialized_object-class"></a>uninitialized_object 類別

當使用未初始化的物件時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[uninitialized_object 的構造函式](#uninitialized_object)|初始化 `uninitialized_object` 類別的新執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="uninitialized_object"></a>uninitialized_object

`uninitialized_object` 例外狀況的新實例。

### <a name="syntax"></a>語法

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

`uninitialized_object` 的 exception 物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
