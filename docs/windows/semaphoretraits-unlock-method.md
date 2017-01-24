---
title: "SemaphoreTraits::Unlock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SemaphoreTraits::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

釋放共用資源的控制項。  
  
## 語法  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### 參數  
 `h`  
 為號誌物件的控制代碼。  
  
## 備註  
 如果開啟作業失敗，Unlock\(\) 發出表示失敗原因的錯誤。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [SemaphoreTraits 結構](../windows/semaphoretraits-structure.md)