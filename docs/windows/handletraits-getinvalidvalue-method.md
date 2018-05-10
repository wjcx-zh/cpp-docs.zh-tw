---
title: 'Handletraits:: Getinvalidvalue 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 190c327a404d19da86fdb86c32411a8ffeb06e7c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="handletraitsgetinvalidvalue-method"></a>HANDLETraits::GetInvalidValue 方法
表示無效的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
inline static HANDLE GetInvalidValue();  
```  
  
## <a name="return-value"></a>傳回值  
 一律傳回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 由 Windows 所定義）。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [HANDLETraits 結構](../windows/handletraits-structure.md)