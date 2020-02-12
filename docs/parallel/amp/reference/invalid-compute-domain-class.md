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
ms.openlocfilehash: 3b8179e8e92665fa6482bd092504af71aa0106f0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126457"
---
# <a name="invalid_compute_domain-class"></a>invalid_compute_domain 類別

當執行時間無法使用在[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)呼叫位置指定的計算網域來啟動核心時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[invalid_compute_domain 的構造函式](#ctor)|初始化 `invalid_compute_domain` 類別的新執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="ctor"></a>invalid_compute_domain

初始化  類別的新執行個體。

## <a name="syntax"></a>語法

```cpp
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

`invalid_compute_domain` 類別的實例

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
