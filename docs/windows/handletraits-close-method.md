---
title: 'Handletraits:: Close 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 3c631a7c-ccce-472a-b1da-aab8fa815c13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f45f95fb1b060f3892def6dc2962bfffef70c77
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="handletraitsclose-method"></a>HANDLETraits::Close 方法
關閉指定的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 若要關閉控制代碼。  
  
## <a name="return-value"></a>傳回值  
 **true**如果處理`h`關閉成功，否則**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [HANDLETraits 結構](../windows/handletraits-structure.md)