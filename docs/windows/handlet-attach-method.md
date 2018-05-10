---
title: 'Handlet:: Attach 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: a8783a18-bbf6-456c-98a3-e2048a10d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f7e70ec50ca76f1a7a525416b33d5eac46c08a4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="handletattach-method"></a>HandleT::Attach 方法
將指定的控制代碼與目前 HandleT 物件產生關聯。  
  
## <a name="syntax"></a>語法  
  
```  
void Attach(  
   typename HandleTraits::Type h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 控制代碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)