---
title: 'Handlet:: Internalclose 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b0aef97645d515a03dcf2cab90eedc06f07971c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose 方法
關閉目前的 HandleT 物件。  
  
## <a name="syntax"></a>語法  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>傳回值  
 `true` 如果目前 HandleT 關閉順利啟動。否則， `false`。  
  
## <a name="remarks"></a>備註  
 InternalClose() 受到保護。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)