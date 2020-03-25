---
title: AsyncResultType 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: b8a2a9ec803fba1be0012fcb58bf3b42e78f9071
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214158"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列舉

指定 `GetResults()` 方法所傳回的結果類型。

## <a name="syntax"></a>語法

```cpp
enum AsyncResultType;
```

## <a name="members"></a>成員

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`MultipleResults`|一組多個結果，會在 `Start` 狀態和呼叫 `Close()` 之前逐漸呈現。|
|`SingleResult`|單一結果，會在 `Complete` 事件發生後出現。|

## <a name="requirements"></a>需求

**標頭：** async。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
