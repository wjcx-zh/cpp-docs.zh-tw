---
title: "AsyncBase::CurrentStatus 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::CurrentStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CurrentStatus 方法"
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::CurrentStatus 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取目前的非同步作業的狀態。  
  
## 語法  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### 參數  
 `status`  
 這個作業儲存目前狀態的位置。  
  
## 備註  
 這個運算是安全執行緒。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)   
 [AsyncStatusInternal 列舉](../windows/asyncstatusinternal-enumeration.md)