---
title: ArgTraitsHelper 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe97cc63de1f83d110e37451c1ceb91c7ad59f49
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652457"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 結構
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<typename TDelegateInterface>  
struct ArgTraitsHelper;  
```  
  
### <a name="parameters"></a>參數  
 *TDelegateInterface*  
 委派的介面。  
  
## <a name="remarks"></a>備註  
 可協助定義委派引數的一般的特性。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`methodType`|`decltype(&TDelegateInterface::Invoke)` 的同義字。|  
|`Traits`|`ArgTraits<methodType>` 的同義字。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[ArgTraitsHelper::args 常數](../windows/argtraitshelper-args-constant.md)|可協助[argtraits:: Args](../windows/argtraits-args-constant.md)上保留的參數數目的計數`Invoke`委派介面的方法。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)