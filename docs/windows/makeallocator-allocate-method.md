---
title: 'Makeallocator:: Allocate 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0e8d387dea7687ad61d85f975d58aa47489266d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
__forceinline void* Allocate();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，配置的記憶體的指標否則， `nullptr`。  
  
## <a name="remarks"></a>備註  
 配置記憶體，並將它與目前 MakeAllocator 物件產生關聯。  
  
 配置大小是記憶體的目前 MakeAllocator 範本參數所指定之類型的大小。  
  
 開發人員必須覆寫只 Allocate() 方法以實作不同的記憶體配置模式。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [MakeAllocator 類別](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)