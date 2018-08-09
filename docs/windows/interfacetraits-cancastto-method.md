---
title: 'Interfacetraits:: Cancastto 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2f8712e06838fb2d2269ba307a551997d7bd57c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018227"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>參數  
 *ptr*  
 類型的指標的名稱。  
  
 *riid*  
 介面 ID `Base`。  
  
 *ppv*  
 如果這項作業成功， *ppv*指向所指定之介面`Base`。 否則，請*ppv*設為**nullptr**。  
  
## <a name="return-value"></a>傳回值  
 **則為 true**這項作業成功時並*ptr*轉換成指標`Base`，否則**false** 。  
  
## <a name="remarks"></a>備註  
 指出指定的指標是否可以轉換成指標`Base`。  
  
 如需詳細資訊`Base`，請參閱 <<c2>  **公用 Typedefs**一節中[InterfaceTraits 結構](../windows/interfacetraits-structure.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)