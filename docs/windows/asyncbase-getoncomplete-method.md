---
title: "AsyncBase::GetOnComplete 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::GetOnComplete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOnComplete 方法"
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::GetOnComplete 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製目前完成事件處理常式的位址到指定的變數。  
  
## 語法  
  
```  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
#### 參數  
 `completeHandler`  
 儲存目前事件處理常式的位址的位置。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_ILLEGAL\_METHOD\_CALL。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)