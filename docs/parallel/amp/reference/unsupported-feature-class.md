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
ms.openlocfilehash: 7635f999b227d02ec7fd56296fef1b0b047abd29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405465"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature 類別

使用不支援的功能時，會擲回例外狀況。

## <a name="syntax"></a>語法

```
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[unsupported_feature 建構函式](#unsupported_feature)|建構的新執行個體`unsupported_feature`例外狀況。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupportedfeature"></a>unsupported_feature

  建構的新執行個體`unsupported_feature`例外狀況。

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

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** 並行

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
