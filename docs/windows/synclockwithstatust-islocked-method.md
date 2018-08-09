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
ms.openlocfilehash: 80c744431fe7df32be705fcf91eef0a8691b8fa4
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015794"
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