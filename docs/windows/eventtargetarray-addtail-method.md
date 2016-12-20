---
title: "EventTargetArray::AddTail 方法 | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::EventTargetArray::AddTail"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddTail 方法"
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventTargetArray::AddTail 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
void AddTail(  
   _In_ IUnknown* element  
);  
```  
  
#### 參數  
 `element`  
 附加的事件處理常式的指標。  
  
## 備註  
 將指定的附加的事件處理常式至內部群組的結束事件處理常式。  
  
 AddTail \(\) EventSource 只適合由類別在內部使用。  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [EventTargetArray 類別](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)