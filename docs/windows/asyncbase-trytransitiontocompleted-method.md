---
title: "AsyncBase::TryTransitionToCompleted 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryTransitionToCompleted 方法"
ms.assetid: 8d038e0a-47ec-4cfc-8aeb-6821282df67a
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::TryTransitionToCompleted 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指出目前非同步作業是否已經完成。  
  
## 語法  
  
```  
bool TryTransitionToCompleted(  
   void  
);  
```  
  
## 傳回值  
 如果非同步作業完成，則為 `true`，否則為 `false`。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)