---
title: improper_lock 類別
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: de7393c9186a1572040acd18854b5b3046b239f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552785"
---
# <a name="improperlock-class"></a>improper_lock 類別

這個類別描述以不當的方式取得鎖定時擲回的例外狀況。

## <a name="syntax"></a>語法

```
class improper_lock : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[improper_lock](#ctor)|多載。 建構 `improper_lock exception`。|

## <a name="remarks"></a>備註

一般而言，當嘗試取得不可重新進入鎖定以遞迴方式，在相同的內容時，便會擲回這個例外狀況。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`improper_lock`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> improper_lock

建構 `improper_lock exception`。

```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>參數

*訊息 （_m)*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[critical_section 類別](critical-section-class.md)<br/>
[reader_writer_lock 類別](reader-writer-lock-class.md)
