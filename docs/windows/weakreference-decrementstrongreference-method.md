---
title: 'Weakreference:: Decrementstrongreference 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5c7e2161c5451fe82e12918f00e8cb2cde37d336
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642311"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>備註  
 目前的強式的參考計數的遞減**WeakReference**物件。  
  
 當強式參考計數變成零時，強式參考會設定為**nullptr**。  
  
## <a name="return-value"></a>傳回值  
 遞減的強式參考計數。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [WeakReference 類別](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)