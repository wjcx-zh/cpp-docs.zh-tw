---
title: InterfaceTraits 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b4b219091393b1195b60ae78347f952c2c9d37a
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 結構
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<typename CloakedType>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### <a name="parameters"></a>參數  
 `I0`  
 介面的名稱。  
  
 `CloakedType`  
 RuntimeClass、 Implements 和 ChainInterfaces，支援介面 Id 的清單中不是介面。  
  
## <a name="remarks"></a>備註  
 實作介面的特性相同。  
  
 第二個範本是特製化隱匿的介面。 第三個範本是特製化 Nil 的參數。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`Base`|`I0` 範本參數的同義字。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo 方法](../windows/interfacetraits-cancastto-method.md)|指出指定的指標是否可以轉換成指標`Base`。|  
|[InterfaceTraits::CastToBase 方法](../windows/interfacetraits-casttobase-method.md)|會轉換為指標的指定的指標`Base`。|  
|[InterfaceTraits::CastToUnknown 方法](../windows/interfacetraits-casttounknown-method.md)|將轉換的 IUnknown 指標的指定的指標。|  
|[InterfaceTraits::FillArrayWithIid 方法](../windows/interfacetraits-fillarraywithiid-method.md)|指派的介面 ID`Base`索引引數所指定之陣列項目的。|  
|[InterfaceTraits::Verify 方法](../windows/interfacetraits-verify-method.md)|確認已正確衍生基底。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[InterfaceTraits::IidCount 常數](../windows/interfacetraits-iidcount-constant.md)|保存介面識別碼相關聯的目前 InterfaceTraits 物件的數目。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `InterfaceTraits`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)