---
title: uninitialized_object 類別
ms.date: 11/04/2016
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: 1c431364aee0f1d1e75059abdb023ae52cf92155
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279325"
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
|[uninitialized_object 建構函式](#ctor)|初始化 `uninitialized_object` 類別的新執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行
## <a name="uninitialized_object__ctor"></a> unsupported_feature

建構 unsupported_feature 例外狀況的新執行個體。

### <a name="syntax"></a>語法

```
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

`unsupported_feature` 物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
