---
title: 'Weakreference:: Incrementstrongreference 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee53e068c13f52c01e997680b57915051a8efad8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>傳回值  
 遞增的強式參考計數。  
  
## <a name="remarks"></a>備註  
 目前的 WeakReference 物件的強式參考計數遞增。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
[WeakReference 類別](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)