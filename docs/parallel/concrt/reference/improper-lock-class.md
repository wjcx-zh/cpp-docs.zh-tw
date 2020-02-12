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
ms.openlocfilehash: 886444f3e856234be010715a8ee0c707cf919bb4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142392"
---
# <a name="improper_lock-class"></a>improper_lock 類別

這個類別描述以不當的方式取得鎖定時擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[improper_lock](#ctor)|已多載。 建構 `improper_lock exception`。|

## <a name="remarks"></a>備註

一般來說，嘗試在相同的內容上以遞迴方式取得不可重新進入的鎖定時，就會擲回這個例外狀況。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`improper_lock`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>improper_lock

建構 `improper_lock exception`。

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[critical_section 類別](critical-section-class.md)<br/>
[reader_writer_lock 類別](reader-writer-lock-class.md)
