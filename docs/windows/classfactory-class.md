---
title: "ClassFactory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory
dev_langs: C++
helpviewer_keywords: ClassFactory class
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c37c016809d31fcb072f23768e9f54313331016
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="classfactory-class"></a>ClassFactory 類別
實作 IClassFactory 介面的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `I0`  
 第零個介面。  
  
 `I1`  
 第一個介面。  
  
 `I2`  
 第二個介面中。  
  
## <a name="remarks"></a>備註  
 利用`ClassFactory`提供使用者定義的 factory 實作。  
  
 下列的程式設計模式，將示範如何使用[實作](../windows/implements-structure.md)結構，以指定三個以上的介面上的 class factory。  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ClassFactory::ClassFactory 建構函式](../windows/classfactory-classfactory-constructor.md)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ClassFactory::AddRef 方法](../windows/classfactory-addref-method.md)|遞增目前 ClassFactory 物件的參考計數。|  
|[ClassFactory::LockServer 方法](../windows/classfactory-lockserver-method.md)|遞增或遞減數目基礎物件，會追蹤目前 ClassFactory 物件。|  
|[ClassFactory::QueryInterface 方法](../windows/classfactory-queryinterface-method.md)|擷取指定參數的介面指標。|  
|[ClassFactory::Release 方法](../windows/classfactory-release-method.md)|遞減目前 ClassFactory 物件的參考計數。|  
  
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
  
## <a name="see-also"></a>請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)