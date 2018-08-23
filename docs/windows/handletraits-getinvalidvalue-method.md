---
title: 'Handletraits:: Getinvalidvalue 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 82616b0fc8cda44ea501b87f6ac1c6e0eddbfb57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609358"
---
# <a name="handletraitsgetinvalidvalue-method"></a>HANDLETraits::GetInvalidValue 方法

表示無效的控制代碼。

## <a name="syntax"></a>語法

```cpp
inline static HANDLE GetInvalidValue();
```

## <a name="return-value"></a>傳回值

一律會傳回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 是由 Windows 定義）。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>另請參閱

[HANDLETraits 結構](../windows/handletraits-structure.md)