---
title: 'Handlet:: Detach 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 100d215099494c9b2714fd2c42dee69644a5006c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878459"
---
# <a name="handletdetach-method"></a>HandleT::Detach 方法
取消目前 HandleT 物件從其基礎控制代碼的關聯。  
  
## <a name="syntax"></a>語法  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>傳回值  
 基礎控制代碼。  
  
## <a name="remarks"></a>備註  
 這項作業完成時，會將目前 HandleT 設定為無效的狀態。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)