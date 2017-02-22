---
title: "SimpleActivationFactory::ActivateInstance 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivateInstance 方法"
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleActivationFactory::ActivateInstance 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立指定介面的執行個體。  
  
## 語法  
  
```  
STDMETHOD(  
   ActivateInstance  
)(_Deref_out_ IInspectable **ppvObject);  
```  
  
#### 參數  
 `ppvObject`  
 這個作業完成時，`Base` 類別樣板參數所指定的物件執行個體的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 備註  
 如果 \_\_WRL\_STRICT 已定義，且如果類別樣板參數指定的基底類別不是衍生自 [RuntimeClass](../windows/runtimeclass-class.md)，或未使用 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值設定，就會判斷錯誤發出，。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)