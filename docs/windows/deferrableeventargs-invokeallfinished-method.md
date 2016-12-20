---
title: "DeferrableEventArgs::InvokeAllFinished 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DeferrableEventArgs::InvokeAllFinished 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

呼叫此方法，表示已完成延期事件的所有處理。  
  
## 語法  
  
```cpp  
void InvokeAllFinished()  
```  
  
## 備註  
 您應該在事件來源呼叫 [InvokeAll](../windows/eventsource-invokeall-method.md) 之後，呼叫這個方法。  呼叫這個方法能避免其他延期，並在沒有採取任何延期時，強制執行完成處理常式。  
  
 如需程式碼範例，請參閱 [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)。  
  
## 需求  
 **標頭：**event.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)