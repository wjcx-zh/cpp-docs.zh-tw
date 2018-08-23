---
title: 'Handlenulltraits:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 155fb5a07f747e4107e630b0db65d321ee726e2c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602212"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close 方法

關閉指定的控制代碼。

## <a name="syntax"></a>語法

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*h*  
若要關閉控制代碼。

## <a name="return-value"></a>傳回值

**真**如果處理*h*關閉順利完成，否則**false**。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>另請參閱

[HANDLENullTraits 結構](../windows/handlenulltraits-structure.md)