---
title: "HandleT::Attach 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
ms.assetid: a8783a18-bbf6-456c-98a3-e2048a10d79f
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HandleT::Attach 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的控制代碼與目前 HandleT 物件關聯。  
  
## 語法  
  
```  
void Attach(  
   typename HandleTraits::Type h  
);  
```  
  
#### 參數  
 `h`  
 控制代碼。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)