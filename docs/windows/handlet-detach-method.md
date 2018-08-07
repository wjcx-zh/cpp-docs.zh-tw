---
title: 'Handlet:: Detach 方法 |Microsoft Docs'
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
ms.openlocfilehash: cc11d6be992584adb1ce2075e73d080cc3a43f47
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569475"
---
# <a name="handletdetach-method"></a>HandleT::Detach 方法
取消目前的關聯**HandleT**從其基礎控制代碼的物件。  
  
## <a name="syntax"></a>語法  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>傳回值  
 基礎控制代碼。  
  
## <a name="remarks"></a>備註  
 這項作業完成時，目前**HandleT**設為無效的狀態。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)