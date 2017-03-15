---
title: "AsyncBase::ContinueAsyncOperation 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ContinueAsyncOperation 方法"
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::ContinueAsyncOperation 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

判斷非同步作業是否應該繼續處理或應該中止。  
  
## 語法  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## 傳回值  
 `true` ，如果非同步作業的目前狀態是 *started*，表示作業應該繼續。  否則， `false`，表示作業應該中止。  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)