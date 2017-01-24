---
title: "HandleT::InternalClose 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InternalClose 方法"
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::InternalClose 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

關閉目前 HandleT 物件。  
  
## 語法  
  
```  
virtual bool InternalClose();  
```  
  
## 傳回值  
 `true` ，如果目前 HandleT 成功關閉，否則， `false`。  
  
## 備註  
 InternalClose \(\) 會受到保護。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)