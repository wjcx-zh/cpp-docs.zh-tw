---
title: "Synclockwithstatust:: Islocked 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs: C++
helpviewer_keywords: IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05892ef6448821783fb7017ac8373423e5d37783
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
bool IsLocked() const;  
```  
  
## <a name="remarks"></a>備註  
 指出目前的 SyncLockWithStatusT 物件是否擁有資源;SyncLockWithStatusT 物件也就是具有*鎖定*。  
  
## <a name="return-value"></a>傳回值  
 **true** SyncLockWithStatusT 物件已鎖定，否則，如果**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>請參閱  
 [SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)