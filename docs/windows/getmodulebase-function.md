---
title: "GetModuleBase 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::GetModuleBase"
dev_langs: 
  - "C++"
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# GetModuleBase 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取允許遞增和遞減 [RuntimeClass](../windows/runtimeclass-class.md) 物件的參考計數的 [ModuleBase](../windows/modulebase-class.md) 指標。  
  
## 語法  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## 傳回值  
 `ModuleBase` 物件的指標。  
  
## 備註  
 這個函式會在內部使用，會遞增或遞減物件參考計數。  
  
 您可以使用這個函式會呼叫 [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) 和 [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md)控制項參考計數。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)