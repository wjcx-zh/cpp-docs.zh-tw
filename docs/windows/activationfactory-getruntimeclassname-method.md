---
title: "ActivationFactory::GetRuntimeClassName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetRuntimeClassName 方法"
ms.assetid: 74e34f0a-9c51-4b40-89f5-45c6c5886ece
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::GetRuntimeClassName 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得目前 ActivationFactory 具現化物件的執行階段類別名稱。  
  
## 語法  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### 參數  
 `runtimeName`  
 這個作業完成時，會包含物件執行階段類別名稱目前 ActivationFactory 具現化之字串的控制代碼。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述失敗的 HRESULT。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ActivationFactory 類別](../windows/activationfactory-class.md)