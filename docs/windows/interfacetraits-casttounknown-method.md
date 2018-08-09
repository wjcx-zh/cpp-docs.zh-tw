---
title: 'Interfacetraits:: Casttounknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bdb87fe43b5cc6a5d2c141ac534e3b5e781f91e8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019913"
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename T>  
static __forceinline IUnknown* CastToUnknown(  
   _In_ T* ptr  
);  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 參數的型別*ptr*。  
  
 *ptr*  
 類型指標*T*。  
  
## <a name="return-value"></a>傳回值  
 IUnknown 指標從中`Base`衍生。  
  
## <a name="remarks"></a>備註  
 轉換指標的指定的指標`IUnknown`。  
  
 如需詳細資訊`Base`，請參閱公用 Typedefs 一節[InterfaceTraits 結構](../windows/interfacetraits-structure.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [InterfaceTraits 結構](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)