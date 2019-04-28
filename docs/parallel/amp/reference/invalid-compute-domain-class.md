---
title: invalid_compute_domain 類別
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 51fcd9e42bc4497131da5adb3dff72efb46537b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351715"
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain 類別

執行階段無法使用在指定的計算網域啟動核心時，會擲回的例外狀況[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)呼叫站台。

## <a name="syntax"></a>語法

```
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_compute_domain 建構函式](#ctor)|初始化 `invalid_compute_domain` 類別的新執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行

## <a name="ctor"></a> invalid_compute_domain

初始化類別的新執行個體。

## <a name="syntax"></a>語法

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

執行個體`invalid_compute_domain`類別

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
