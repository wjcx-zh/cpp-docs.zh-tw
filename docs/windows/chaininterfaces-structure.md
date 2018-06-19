---
title: ChainInterfaces 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
dev_langs:
- C++
helpviewer_keywords:
- ChainInterfaces structure
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18814a4ad87cefa39201d369926c0778931d4d64
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861132"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces 結構
指定可以套用至一組介面 ID 的驗證和初始化函式。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### <a name="parameters"></a>參數  
 `I0`  
 （必要）介面識別碼 0。  
  
 `I1`  
 （必要）介面 ID 1。  
  
 `I2`  
 （選擇性）介面 ID 2。  
  
 `I3`  
 （選擇性）介面 ID 3。  
  
 `I4`  
 （選擇性）介面 ID 4。  
  
 `I5`  
 （選擇性）介面識別碼 5。  
  
 `I6`  
 （選擇性）介面識別碼 6。  
  
 `I7`  
 （選擇性）介面 ID 7。  
  
 `I8`  
 （選擇性）介面 ID 8。  
  
 `I9`  
 （選擇性）介面 ID 9。  
  
 `DerivedType`  
 衍生的型別。  
  
 `BaseType`  
 衍生類型的基底類型。  
  
 `hasImplements`  
 布林值，如果`true`，表示您無法使用[MixIn](../windows/mixin-structure.md)不是衍生自的類別結構[實作](../windows/implements-structure.md)stucture。  
  
## <a name="members"></a>成員  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ChainInterfaces::CanCastTo 方法](../windows/chaininterfaces-cancastto-method.md)|指出指定的介面識別碼可轉換成每個特製化 ChainInterface 範本參數所定義。|  
|[ChainInterfaces::CastToUnknown 方法](../windows/chaininterfaces-casttounknown-method.md)|會轉換為類型所定義的介面指標`I0`IUnknown 指標的樣板參數。|  
|[ChainInterfaces::FillArrayWithIid 方法](../windows/chaininterfaces-fillarraywithiid-method.md)|存放區所定義的介面 ID`I0`介面識別碼指定陣列中的指定位置的樣板參數。|  
|[ChainInterfaces::Verify 方法](../windows/chaininterfaces-verify-method.md)|確認每個介面定義的範本參數`I0`透過`I9`繼承自 IUnknown 和/或 IInspectable，而且`I0`繼承自`I1`透過`I9`。|  
  
### <a name="protected-constants"></a>受保護的常數  
  
|名稱|描述|  
|----------|-----------------|  
|[ChainInterfaces::IidCount 常數](../windows/chaininterfaces-iidcount-constant.md)|介面 Id 的範本參數所指定的介面中所包含的總數`I0`透過`I9`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `I0`  
  
 `ChainInterfaces`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)