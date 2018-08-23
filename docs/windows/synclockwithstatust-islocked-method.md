---
title: 'Synclockwithstatust:: Islocked 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d70a2c316f9e7994292f3dc29cef5bce993778ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595059"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
bool IsLocked() const;
```

## <a name="remarks"></a>備註

指出是否目前**SyncLockWithStatusT**物件擁有資源，也就是，則**SyncLockWithStatusT**物件*鎖定*。

## <a name="return-value"></a>傳回值

**真**如果**SyncLockWithStatusT**物件是否已鎖定，否則**false**。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>另請參閱

[SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)