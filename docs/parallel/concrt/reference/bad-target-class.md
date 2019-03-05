---
title: bad_target 類別
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 04489151cedf1a47aeebd883e76b8d26b51031ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298616"
---
# <a name="badtarget-class"></a>bad_target 類別

這個類別描述在傳訊區塊獲得目標的指標，但該目標對所執行的作業來說並不正確時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```
class bad_target : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[bad_target](#ctor)|多載。 建構 `bad_target` 物件。|

## <a name="remarks"></a>備註

這個例外狀況通常會擲回的原因，例如做為目標，嘗試使用不同的目標保留的訊息，或釋出其並未持有的保留項目。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`bad_target`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> bad_target

建構 `bad_target` 物件。

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)
