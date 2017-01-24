---
title: "SemaphoreTraits 結構 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SemaphoreTraits 結構"
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SemaphoreTraits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 Semaphore 物件的通用特性。  
  
## 語法  
  
```  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[SemaphoreTraits::Unlock 方法](../windows/semaphoretraits-unlock-method.md)|釋放共用資源的控制項。|  
  
## 繼承階層架構  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits Namespace](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)