---
title: "EventTargetArray::EventTargetArray 建構函式 | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventTargetArray，建構函式"
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventTargetArray::EventTargetArray 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### 參數  
 `hr`  
 在這個建構函式 \(Constructor\) 作業之後，參數 `hr` 指示陣列的配置是成功還是失敗。  下表列出 `hr` 可能的值。  
  
 S\_OK  
 作業已成功。  
  
 E\_OUTOFMEMORY  
 無法為陣列配置記憶體。  
  
 S\_FALSE  
 參數`items` 小於或等於零。  
  
 `items`  
 要配置的陣列元素數目。  
  
## 備註  
 初始化 EventTargetArray 類別的新執行個體。  
  
 EventTargetArray 是用來在 EventSource 物件中保留一組事件處理常式陣列用的。  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [EventTargetArray 類別](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)