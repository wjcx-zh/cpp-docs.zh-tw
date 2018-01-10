---
title: "Modulebase:: Decrementobjectcount 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
dev_langs: C++
helpviewer_keywords: DecrementObjectCount method
ms.assetid: a016fb07-a36e-40cd-bc7b-8f6e85e256e7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2a8679c82c3ea699c5b3842ca969f75cd5af9d68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="modulebasedecrementobjectcount-method"></a>ModuleBase::DecrementObjectCount 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
virtual long DecrementObjectCount() = 0;  
```  
  
## <a name="return-value"></a>傳回值  
 遞減作業之前計數。  
  
## <a name="remarks"></a>備註  
 實作時，遞減模組所追蹤的物件數目。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [ModuleBase 類別](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)