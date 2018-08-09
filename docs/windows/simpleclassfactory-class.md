---
title: SimpleClassFactory 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleClassFactory class
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 21b52876cb2a6c7bbf110a06cdfb29abdf1930d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641818"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 類別
提供基本機制以建立基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Base>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
### <a name="parameters"></a>參數  
 *基底*  
 基底類別。  
  
## <a name="remarks"></a>備註  
 基底類別必須提供預設建構函式。  
  
 下列程式碼範例示範如何使用**SimpleClassFactory**具有[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)巨集。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[SimpleClassFactory::CreateInstance 方法](../windows/simpleclassfactory-createinstance-method.md)|建立指定之介面的執行個體。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ClassFactory`  
  
 `SimpleClassFactory`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)