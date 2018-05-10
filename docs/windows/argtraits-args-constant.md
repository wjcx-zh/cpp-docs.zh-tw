---
title: 'Argtraits:: Args 常數 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f87b29634d5b9acef2e2ccb3f7b4d5f227433d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args 常數
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>備註  
 保留的叫用方法的委派介面上的參數數目的計數。  
  
## <a name="remarks"></a>備註  
 當`args`等於-1 表示可以有沒有相符的叫用方法簽章。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [ArgTraits 結構](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)