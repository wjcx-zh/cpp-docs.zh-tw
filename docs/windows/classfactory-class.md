---
title: ClassFactory 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
dev_langs:
- C++
helpviewer_keywords:
- ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9a7caba7ccfb8f5764a1f460835ff540c838975
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641037"
---
# <a name="classfactory-class"></a>ClassFactory 類別
實作 `IClassFactory` 介面的基本功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ClassFactory : public Details::RuntimeClass<  
   typename Details::InterfaceListHelper<IClassFactory,   
   I0,   
   I1,   
   I2,   
   Details::Nil>::TypeT,   
   RuntimeClassFlags<ClassicCom | InhibitWeakReference>,   
      false>;  
```  
  
### <a name="parameters"></a>參數  
 *I0*  
 第零個介面中。  
  
 *I1*  
 第一個介面。  
  
 *I2*  
 第二個介面中。  
  
## <a name="remarks"></a>備註  
 利用**ClassFactory**以提供使用者定義的 factory 實作。  
  
 下列的程式設計模式將示範如何使用[實作](../windows/implements-structure.md)結構，以指定三個以上的介面上的 class factory。  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ClassFactory::ClassFactory 建構函式](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ClassFactory::AddRef 方法](../windows/classfactory-addref-method.md)|目前的參考計數會遞增**ClassFactory**物件。|  
|[ClassFactory::LockServer 方法](../windows/classfactory-lockserver-method.md)|遞增或遞減目前所追蹤物件的基礎數目**ClassFactory**物件。|  
|[ClassFactory::QueryInterface 方法](../windows/classfactory-queryinterface-method.md)|擷取指定參數的介面指標。|  
|[ClassFactory::Release 方法](../windows/classfactory-release-method.md)|遞減參考計數目前**ClassFactory**物件。|  
  
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
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)