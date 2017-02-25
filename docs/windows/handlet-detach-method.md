---
title: "HandleT::Detach 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HandleT::Detach 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

解除目前 HandleT 物件從其基礎控制代碼。  
  
## 語法  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## 傳回值  
 基礎控制代碼。  
  
## 備註  
 當這個作業完成時，目前 HandleT 被設定為無效狀態。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)