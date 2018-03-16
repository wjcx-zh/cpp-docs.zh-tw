---
title: "Comptrrefbase:: Operator IUnknown * * 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs:
- C++
helpviewer_keywords:
- operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04eaa2992c74b4cb46954ac73aa7b5a8ae735f82
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** 運算子
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
operator IUnknown**() const;  
```  
  
## <a name="remarks"></a>備註  
 會轉換目前[ptr_](../windows/comptrrefbase-ptr-data-member.md)資料成員指標--a-指標-將 IUnknown 介面。  
  
 如果目前 ComPtrRefBase 不是衍生自 IUnknown，就會發出錯誤。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [ComPtrRefBase 類別](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)