---
title: ActivationFactory 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6775e9466ed337a070b6a234a4d65bb949a009e4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="activationfactory-class"></a>ActivationFactory 類別
讓 Windows 執行階段啟動一或多個類別。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### <a name="parameters"></a>參數  
 `I0`  
 第零個介面。  
  
 `I1`  
 第一個介面。  
  
 `I2`  
 第二個介面中。  
  
## <a name="remarks"></a>備註  
 ActivationFactory 提供註冊方法和 IActivationFactory 介面的基本功能。 ActivationFactory 也可讓您提供的自訂處理站實作。  
  
 下列程式碼片段以透過符號會說明如何使用 ActivationFactory。  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 下列程式碼片段示範如何使用[實作](../windows/implements-structure.md)結構，以指定三個以上的介面識別碼。  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory 建構函式](../windows/activationfactory-activationfactory-constructor.md)|初始化 ActivationFactory 類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ActivationFactory::AddRef 方法](../windows/activationfactory-addref-method.md)|遞增目前 ActivationFactory 物件的參考計數。|  
|[ActivationFactory::GetIids 方法](../windows/activationfactory-getiids-method.md)|擷取實作的介面 Id 的陣列。|  
|[ActivationFactory::GetRuntimeClassName 方法](../windows/activationfactory-getruntimeclassname-method.md)|取得目前 ActivationFactory 具現化物件的執行階段類別名稱。|  
|[ActivationFactory::GetTrustLevel 方法](../windows/activationfactory-gettrustlevel-method.md)|取得目前 ActivationFactory 具現化物件的信任層級。|  
|[ActivationFactory::QueryInterface 方法](../windows/activationfactory-queryinterface-method.md)|擷取指定之介面的指標。|  
|[ActivationFactory::Release 方法](../windows/activationfactory-release-method.md)|遞減目前 ActivationFactory 物件的參考計數。|  
  
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
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)