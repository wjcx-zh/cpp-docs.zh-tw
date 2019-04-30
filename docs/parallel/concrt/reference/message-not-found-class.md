---
title: message_not_found 類別
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: da0a44b90346959756c1ef7c685bef234fe6e46a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394412"
---
# <a name="messagenotfound-class"></a>message_not_found 類別

這個類別描述在傳訊區塊找不到所要求之訊息時擲回的例外狀況。

## <a name="syntax"></a>語法

```
class message_not_found : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[message_not_found](#ctor)|多載。 建構 `message_not_found` 物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`message_not_found`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> message_not_found

建構 `message_not_found` 物件。

```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)
