---
title: 'Interfacetraits:: Casttobase 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
dev_langs:
- C++
helpviewer_keywords:
- CastToBase method
ms.assetid: 0591a017-0adf-4358-b946-eb0a307ce7f2
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6817f83d40943b871327c56fac692d9a60163de2
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="interfacetraitscasttobase-method"></a>InterfaceTraits::CastToBase 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
static __forceinline Base* CastToBase(  
   _In_ T* ptr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 參數的型別`ptr`。  
  
 `ptr`  
 類型指標`T`。  
  
## <a name="return-value"></a>傳回值  
 指標`Base`。  
  
## <a name="remarks"></a>備註  
 會轉換為指標的指定的指標`Base`。  
  
 如需有關`Base`，請參閱公用 Typedefs 節[InterfaceTraits 結構](../windows/interfacetraits-structure.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)