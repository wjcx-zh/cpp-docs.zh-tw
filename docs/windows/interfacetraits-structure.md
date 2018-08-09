---
title: InterfaceTraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6cb96b90a069c12e65c53158717d9a89fb0aed3d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014096"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 結構
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<typename CloakedType>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
### <a name="parameters"></a>參數  
 *I0*  
 介面的名稱。  
  
 *CloakedType*  
 針對`RuntimeClass`，`Implements`和`ChainInterfaces`，不會在清單中的介面支援的介面識別碼。  
  
## <a name="remarks"></a>備註  
 實作的介面的一般特性。  
  
 第二個範本是特製化隱匿的介面。 第三個範本是特製化 Nil 參數。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`Base`|同義字*I0*樣板參數。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo 方法](../windows/interfacetraits-cancastto-method.md)|指出指定的指標是否可以轉換成指標`Base`。|  
|[InterfaceTraits::CastToBase 方法](../windows/interfacetraits-casttobase-method.md)|轉換指標的指定的指標`Base`。|  
|[InterfaceTraits::CastToUnknown 方法](../windows/interfacetraits-casttounknown-method.md)|轉換指標的指定的指標`IUnknown`。|  
|[InterfaceTraits::FillArrayWithIid 方法](../windows/interfacetraits-fillarraywithiid-method.md)|介面 ID 指派為`Base`索引引數所指定的陣列元素。|  
|[InterfaceTraits::Verify 方法](../windows/interfacetraits-verify-method.md)|確認`Base`正確衍生。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[InterfaceTraits::IidCount 常數](../windows/interfacetraits-iidcount-constant.md)|保存的介面識別碼相關聯的目前數目**InterfaceTraits**物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `InterfaceTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)