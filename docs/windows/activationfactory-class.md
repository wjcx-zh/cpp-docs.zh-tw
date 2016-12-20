---
title: "ActivationFactory 類別 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivationFactory 類別"
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

啟用一或多個 Windows 類別在執行階段之前啟動。  
  
## 語法  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### 參數  
 `I0`  
 第零個介面。  
  
 `I1`  
 第一個介面。  
  
 `I2`  
 第二個介面。  
  
## 備註  
 ActivationFactory 為 IActivationFactory 介面提供登錄方法和基本功能。  ActivationFactory 也可讓您提供自訂 Factory 實作。  
  
 下列程式碼片段符號會說明如何使用 ActivationFactory。  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 下列程式碼片段會顯示如何使用 [實作](../windows/implements-structure.md) 結構指定三個以上的介面 ID。  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[ActivationFactory::ActivationFactory 建構函式](../windows/activationfactory-activationfactory-constructor.md)|初始化 ActivationFactory 類別。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ActivationFactory::AddRef 方法](../windows/activationfactory-addref-method.md)|遞增目前 ActivationFactory 物件的參考計數。|  
|[ActivationFactory::GetIids 方法](../windows/activationfactory-getiids-method.md)|擷取陣列中實作的介面 ID。|  
|[ActivationFactory::GetRuntimeClassName 方法](../windows/activationfactory-getruntimeclassname-method.md)|取得目前 ActivationFactory 具現化物件的執行階段類別名稱。|  
|[ActivationFactory::GetTrustLevel 方法](../windows/activationfactory-gettrustlevel-method.md)|取得目前 ActivationFactory 具現化物件的信任層級。|  
|[ActivationFactory::QueryInterface 方法](../windows/activationfactory-queryinterface-method.md)|擷取指向指定介面的指標。|  
|[ActivationFactory::Release 方法](../windows/activationfactory-release-method.md)|遞減目前 ActivationFactory 物件的參考計數。|  
  
## 繼承階層架構  
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
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)