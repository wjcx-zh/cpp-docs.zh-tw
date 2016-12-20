---
title: "ActivationFactory::AddRef 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory::AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef 方法"
ms.assetid: dfe96189-ddbe-410a-9f8d-5d8ecc8cc7e6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory::AddRef 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遞增目前 ActivationFactory 物件的參考計數。  
  
## 語法  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述失敗的 HRESULT。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ActivationFactory 類別](../windows/activationfactory-class.md)