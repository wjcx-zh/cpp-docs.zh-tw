---
title: 'Weakreference:: Weakreference 建構函式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference, constructor
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e60b23a0c63ce1415765dd1f94863540849f975
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="weakreferenceweakreference-constructor"></a>WeakReference::WeakReference 建構函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>備註  
 初始化的新執行個體[WeakReference 類別](../windows/weakreference-class1.md)。  
  
 WeakReference 物件的強式參考指標初始化為`nullptr`，和強式參考計數會初始化為 1。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
    
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)