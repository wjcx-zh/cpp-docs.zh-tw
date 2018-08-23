---
title: SimpleActivationFactory 類別 |Microsoft Docs
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
ms.openlocfilehash: 0820012c8c22de1287fcb09037212b870a4ff7bf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594794"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 類別

提供基本機制以建立 Windows 執行階段或傳統 COM 基底類別。

## <a name="syntax"></a>語法

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>參數

*基底*  
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
|[SimpleActivationFactory::GetRuntimeClassName 方法](../windows/simpleactivationfactory-getruntimeclassname-method.md)|取得所指定類別的執行個體的執行階段類別名稱*基底*類別範本參數。|
|[SimpleActivationFactory::GetTrustLevel 方法](../windows/simpleactivationfactory-gettrustlevel-method.md)|取得所指定類別的執行個體的信任層級*基底*類別範本參數。|

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