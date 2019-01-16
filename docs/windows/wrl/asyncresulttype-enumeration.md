---
title: AsyncResultType 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: 309ed876c71f453336ecc2ed10eedc07f2a80be8
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335688"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列舉

指定所傳回的結果的型別`GetResults()`方法。

## <a name="syntax"></a>語法

```cpp
enum AsyncResultType;
```

## <a name="members"></a>成員

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`MultipleResults`|多個結果，以漸進方式之間會顯示一組`Start`狀態，以及之前`Close()`呼叫。|
|`SingleResult`|單一的結果之後, 會呈現`Complete`就會發生事件。|

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)