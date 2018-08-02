---
title: ActivationFactory 類別 |Microsoft Docs
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
ms.openlocfilehash: 18ce213d6c4bedd0bcaa2be1af33281ae69f6ad1
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461501"
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
 *I0*  
 第零個介面中。  
  
 *I1*  
 第一個介面。  
  
 *I2*  
 第二個介面中。  
  
## <a name="remarks"></a>備註  
 **ActivationFactory**提供的註冊方法和基本功能`IActivationFactory`介面。 **ActivationFactory**也可讓您提供的自訂處理站實作。  
  
 下列程式碼片段以符號形式會說明如何使用 ActivationFactory。  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 下列程式碼片段示範如何使用[實作](../windows/implements-structure.md)結構，以指定超過三個介面 Id。  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory 建構函式](../windows/activationfactory-activationfactory-constructor.md)|初始化**ActivationFactory**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ActivationFactory::AddRef 方法](../windows/activationfactory-addref-method.md)|目前的參考計數遞增**ActivationFactory**物件。|  
|[ActivationFactory::GetIids 方法](../windows/activationfactory-getiids-method.md)|擷取實作的介面識別碼的陣列。|  
|[ActivationFactory::GetRuntimeClassName 方法](../windows/activationfactory-getruntimeclassname-method.md)|取得物件的執行階段類別名稱，目前**ActivationFactory**具現化。|  
|[ActivationFactory::GetTrustLevel 方法](../windows/activationfactory-gettrustlevel-method.md)|取得目前 ActivationFactory 具現化物件的信任層級。|  
|[ActivationFactory::QueryInterface 方法](../windows/activationfactory-queryinterface-method.md)|擷取指定之介面的指標。|  
|[ActivationFactory::Release 方法](../windows/activationfactory-release-method.md)|遞減參考計數的目前**ActivationFactory**物件。|  
  
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