---
title: "ArgTraits::args 常數 | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::ArgTraits::args"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "args 常數"
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ArgTraits::args 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
static const int args = -1; ;  
```  
  
## 備註  
 持有委派介面的叫用方法的參數數目的計數。  
  
## 備註  
 當`args` 等於\-1時，顯示沒有相符的叫用方法簽章。  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [ArgTraits 結構](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)