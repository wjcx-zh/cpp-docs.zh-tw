---
title: unsupported_feature 類別
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 561f0a258943f6d7e1c0f1b5cae716592c931fbc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127708"
---
# <a name="unsupported_feature-class"></a>unsupported_feature 類別

使用不支援的功能時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unsupported_feature 的構造函式](#unsupported_feature)|`unsupported_feature` 例外狀況的新實例。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a>unsupported_feature

  `unsupported_feature` 例外狀況的新實例。

### <a name="syntax"></a>語法

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述。

### <a name="return-value"></a>傳回值

`unsupported_feature` 物件。

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** 並行

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
