---
title: "Synclockt:: Islocked 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs: C++
helpviewer_keywords: IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47dc99415fd995f144deddb6ca3bc7a4bb419ca5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
bool IsLocked() const;  
```  
  
## <a name="return-value"></a>傳回值  
 **true** SyncLockT 物件已鎖定，否則，如果**false**。  
  
## <a name="remarks"></a>備註  
 指出目前的 SyncLockT 物件是否擁有資源;也就是說，SyncLockT 物件是*鎖定*。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)