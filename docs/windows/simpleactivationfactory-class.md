---
title: SimpleActivationFactory 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d10544a08fa6faebb1434cd00ca80ac30d4570a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889836"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 類別
提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Base>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 基底類別。  
  
## <a name="remarks"></a>備註  
 基底類別必須提供預設建構函式。  
  
 下列程式碼範例示範如何使用與 SimpleActivationFactory [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)巨集。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance 方法](../windows/simpleactivationfactory-activateinstance-method.md)|建立指定之介面的執行個體。|  
|[SimpleActivationFactory::GetRuntimeClassName 方法](../windows/simpleactivationfactory-getruntimeclassname-method.md)|取得所指定的類別的執行個體的執行階段類別名稱`Base`類別樣板參數。|  
|[SimpleActivationFactory::GetTrustLevel 方法](../windows/simpleactivationfactory-gettrustlevel-method.md)|取得所指定的類別的執行個體的信任層級`Base`類別樣板參數。|  
  
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
  
 `ActivationFactory`  
  
 `SimpleActivationFactory`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)