---
title: 實作結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
dev_langs:
- C++
helpviewer_keywords:
- Implements structure
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1ecbf0b77feef7abeb67f8d0dc300da067d1f2da
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880912"
---
# <a name="implements-structure"></a>Implements 結構
實作指定介面的 QueryInterface 和 GetIid。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
#### <a name="parameters"></a>參數  
 `I0`  
 第零個介面識別碼。 （必要項）。  
  
 `I1`  
 第一個介面識別碼。 (選擇項)  
  
 `I2`  
 第二個介面識別碼。 (選擇項)  
  
 `I3`  
 第三個介面識別碼。 (選擇項)  
  
 `I4`  
 第四個介面識別碼。 (選擇項)  
  
 `I5`  
 第五個介面識別碼。 (選擇項)  
  
 `I6`  
 第六個介面識別碼。 (選擇項)  
  
 `I7`  
 第七個介面識別碼。 (選擇項)  
  
 `I8`  
 兩個的介面識別碼。 (選擇項)  
  
 `I9`  
 第九個介面識別碼。 (選擇項)  
  
 `flags`  
 此類別設定旗標。 一或多個[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)中指定的列舉型別[RuntimeClassFlags](../windows/runtimeclassflags-structure.md)結構。  
  
## <a name="remarks"></a>備註  
 衍生自指定之介面的清單，並實作 helper 範本的 QueryInterface 和 GetIid。  
  
 每個`I0`透過`I9`介面參數必須衍生自 IInspectable，可能是 IUnknown 或[ChainInterfaces](../windows/chaininterfaces-structure.md)範本。 `flags`參數會決定是否產生支援 IUnknown 或 IInspectable。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`ClassFlags`|`RuntimeClassFlags<WinRt>` 的同義字。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Implements::CanCastTo 方法](../windows/implements-cancastto-method.md)|取得指定的介面指標。|  
|[Implements::CastToUnknown 方法](../windows/implements-casttounknown-method.md)|取得基礎 IUnknown 介面指標。|  
|[Implements::FillArrayWithIid 方法](../windows/implements-fillarraywithiid-method.md)|將插入至指定的陣列項目目前的第零個範本參數所指定的介面 ID。|  
  
### <a name="protected-constants"></a>受保護的常數  
  
|名稱|描述|  
|----------|-----------------|  
|[Implements::IidCount 常數](../windows/implements-iidcount-constant.md)|保存實作的介面 Id 的數目。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)