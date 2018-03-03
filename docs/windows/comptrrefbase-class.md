---
title: "ComPtrRefBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRefBase class
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 071598c83086afe12e1d19ef541dbfb3d0dbc55a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 類別
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md)型別或型別衍生自它不只是 ComPtr 所代表的介面。  
  
## <a name="remarks"></a>備註  
 表示基底類別[ComPtrRef](../windows/comptrref-class.md)類別。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`InterfaceType`|範本參數的型別同義`T`。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtrRefBase::operator IInspectable** 運算子](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|會轉換目前[ptr_](../windows/comptrrefbase-ptr-data-member.md)資料成員指標--a-指標-將 IInspectable 介面。|  
|[ComPtrRefBase::operator IUnknown** 運算子](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|會轉換目前[ptr_](../windows/comptrrefbase-ptr-data-member.md)資料成員指標--a-指標-將 IUnknown 介面。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtrRefBase::ptr_ 資料成員](../windows/comptrrefbase-ptr-data-member.md)|目前的範本參數所指定之類型的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ComPtrRefBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)