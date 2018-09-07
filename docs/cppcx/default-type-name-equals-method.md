---
title: '預設:: (type_name):: Equals 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::Object::Equals
dev_langs:
- C++
ms.assetid: 4450f835-06fc-4758-8d0a-72cf00007873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 127f5ee876790fa3cfb8a052c2db6c41cc00f332
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109015"
---
# <a name="defaulttypenameequals-method"></a>default::(type_name)::Equals 方法

判斷指定的物件是否等於目前的物件。

## <a name="syntax"></a>語法

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>參數

*obj*<br/>
要比較的物件。

### <a name="return-value"></a>傳回值

如果物件相等則為`true` ，否則為 `false`。

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** default

**標頭：** vccorlib.h

## <a name="see-also"></a>另請參閱

[預設命名空間](../cppcx/default-namespace.md)