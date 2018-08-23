---
title: 'Asyncbase:: Currentstatus 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 193f4d26f7e163707092f3d0bc8f981a02611a22
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603698"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus 方法

擷取目前的非同步作業的狀態。

## <a name="syntax"></a>語法

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>參數

*status*  
這項作業儲存的目前狀態的位置。

## <a name="remarks"></a>備註

這項作業是安全執行緒。

## <a name="requirements"></a>需求

**標頭：** async.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[AsyncBase 類別](../windows/asyncbase-class.md)  
[AsyncStatusInternal 列舉](../windows/asyncstatusinternal-enumeration.md)