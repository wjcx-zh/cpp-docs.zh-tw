---
title: "Interfacetraits:: Cancastto 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d8dfe6c1873d9cf897494eb6157c2be3baeb435
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `ptr`  
 類型的指標的名稱。  
  
 `riid`  
 介面 ID `Base`。  
  
 `ppv`  
 如果這項作業成功，`ppv`指向所指定介面`Base`。 否則，`ppv`設`nullptr`。  
  
## <a name="return-value"></a>傳回值  
 `true`如果此作業成功，`ptr`轉換成指標`Base`，否則`false`。  
  
## <a name="remarks"></a>備註  
 指出指定的指標是否可以轉換成指標`Base`。  
  
 如需有關`Base`，請參閱公用 Typedefs 節[InterfaceTraits 結構](../windows/interfacetraits-structure.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)