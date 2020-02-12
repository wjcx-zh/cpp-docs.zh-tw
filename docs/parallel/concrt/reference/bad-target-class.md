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
ms.openlocfilehash: 023607ff142b7fa39165cc9b5280a8e9345a3645
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142849"
---
# <a name="bad_target-class"></a>bad_target 類別

這個類別描述在傳訊區塊獲得目標的指標，但該目標對所執行的作業來說並不正確時，所擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[bad_target](#ctor)|已多載。 建構 `bad_target` 物件。|

## <a name="remarks"></a>備註

通常會擲回這個例外狀況，原因如下：目標嘗試使用保留給不同目標的訊息，或釋出未保存的保留。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`bad_target`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** concurrency

## <a name="ctor"></a>bad_target

建構 `bad_target` 物件。

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)
