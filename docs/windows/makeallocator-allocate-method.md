---
title: "Makeallocator:: Allocate 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e93cd6b5b8b3489fc18e8b083c0fc59589ebd1d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [MakeAllocator 類別](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)