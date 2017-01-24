---
title: "AsyncBase::PutOnProgress 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::PutOnProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PutOnProgress 方法"
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::PutOnProgress 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定進度事件處理常式的位址為指定的值。  
  
## 語法  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### 參數  
 `progressHandler`  
 進度事件處理常式被設定的位址。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_ILLEGAL\_METHOD\_CALL。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)