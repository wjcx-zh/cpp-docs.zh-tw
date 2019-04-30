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
ms.openlocfilehash: 05c24672531d50fa9bc31587e6c6733fdff21f29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405452"
---
# <a name="uninitializedobject-class"></a>uninitialized_object 類別

使用未初始化的物件時擲回的例外狀況。

## <a name="syntax"></a>語法

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[uninitialized_object 建構函式](#uninitialized_object)|初始化 `uninitialized_object` 類別的新執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行

## <a name="uninitializedobject"></a>uninitialized_object

建構的新執行個體`uninitialized_object`例外狀況。

### <a name="syntax"></a>語法

```
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

`uninitialized_object`例外狀況物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
