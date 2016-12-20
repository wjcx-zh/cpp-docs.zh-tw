---
title: "SimpleActivationFactory 類別 | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SimpleActivationFactory 類別"
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleActivationFactory 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供基本機制來建立 Windows 執行階段或一般 COM 基底類別。  
  
## 語法  
  
```  
template<  
   typename Base  
>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### 參數  
 `Base`  
 基底類別。  
  
## 備註  
 基底類別必須提供預設建構函式。  
  
 下列程式碼範例會示範如何一起使用 [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) 和 SimpleClassFactory 的巨集。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[SimpleActivationFactory::ActivateInstance 方法](../windows/simpleactivationfactory-activateinstance-method.md)|建立指定介面的執行個體。|  
|[SimpleActivationFactory::GetRuntimeClassName 方法](../windows/simpleactivationfactory-getruntimeclassname-method.md)|取得由 `Base` 類別樣板參數所指定的類別的執行個體的執行階段類別名稱。|  
|[SimpleActivationFactory::GetTrustLevel 方法](../windows/simpleactivationfactory-gettrustlevel-method.md)|取得 `Base` 類別樣板參數所指定的類別的執行個體的信任層級。|  
  
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
  
 `ActivationFactory`  
  
 `SimpleActivationFactory`  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)