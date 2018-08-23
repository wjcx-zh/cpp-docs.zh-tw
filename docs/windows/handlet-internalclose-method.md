---
title: 'Handlet:: Internalclose 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc3f01227cb37285f11ef8256d0b101f156871b5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605512"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose 方法

關閉目前**HandleT**物件。

## <a name="syntax"></a>語法

```cpp
virtual bool InternalClose();
```

## <a name="return-value"></a>傳回值

**真**如果目前**HandleT**關閉順利完成，否則**false**。

## <a name="remarks"></a>備註

**InternalClose()** 已**保護**。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HandleT 類別](../windows/handlet-class.md)