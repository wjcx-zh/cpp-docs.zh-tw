---
title: "SimpleClassFactory 類別 | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SimpleClassFactory 類別"
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleClassFactory 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供基本機制的基底類別。  
  
## 語法  
  
```  
template<  
   typename Base  
>  
class SimpleClassFactory : public ClassFactory<>;  
```  
  
#### 參數  
 `Base`  
 基底類別。  
  
## 備註  
 基底類別必須提供預設建構函式。  
  
 下列程式碼範例會示範如何使用 [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) 巨集的 SimpleClassFactory。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[SimpleClassFactory::CreateInstance 方法](../windows/simpleclassfactory-createinstance-method.md)|建立指定介面的執行個體。|  
  
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
  
 `SimpleClassFactory`  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)