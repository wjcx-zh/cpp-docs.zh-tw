---
title: "Module::ReleaseNotifier::Invoke 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::ReleaseNotifier::Invoke"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Invoke 方法"
ms.assetid: f62686fe-74bf-482b-a46b-6a3c09b80e7e
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# Module::ReleaseNotifier::Invoke 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當被實作時，當模組中的最後一個物件被釋放時會呼叫事件處理常式。  
  
## 語法  
  
```  
virtual void Invoke() = 0;  
```  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)