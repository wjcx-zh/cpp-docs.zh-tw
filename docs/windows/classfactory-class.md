---
title: "ClassFactory 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ClassFactory 類別"
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

實作介面 IClassFactory 的基本功能。  
  
## 語法  
  
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
  
#### 參數  
 `I0`  
 第零個介面。  
  
 `I1`  
 第一個介面。  
  
 `I2`  
 第二個介面。  
  
## 備註  
 利用 `ClassFactory` 提供使用者定義的處理站實作。  
  
 下列程式設計模式會示範如何使用 [實作](../windows/implements-structure.md) 結構來指定多於三個介面在一個class factory。  
  
 `struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[ClassFactory::ClassFactory 建構函式](../windows/classfactory-classfactory-constructor.md)||  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[ClassFactory::AddRef 方法](../windows/classfactory-addref-method.md)|遞增目前 ClassFactory 物件的參考計數。|  
|[ClassFactory::LockServer 方法](../windows/classfactory-lockserver-method.md)|遞增或遞減由目前物件 ClassFactory 追蹤基礎物件的數目。|  
|[ClassFactory::QueryInterface 方法](../windows/classfactory-queryinterface-method.md)|擷取指向由參數所指定的介面的指標。|  
|[ClassFactory::Release 方法](../windows/classfactory-release-method.md)|遞減目前 ClassFactory 物件的參考計數。|  
  
## 繼承階層  
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
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)   
 [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md)