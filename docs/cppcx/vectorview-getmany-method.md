---
title: "VectorView::GetMany 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::GetMany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::GetMany 方法"
ms.assetid: 67d9348f-66fe-417e-9e25-5de0a3cd306c
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::GetMany 方法
由指定的索引處開始，從目前 VectorView 擷取一連串項目。  
  
## 語法  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
#### 參數  
 `startIndex`  
 要擷取之開始項目以零為起始的索引。  
  
 `dest`  
 當這項作業完成後，是項目陣列，從 `startIndex` 指定的項目開始，到 VectorView 的最後一個項目結束。  
  
## 傳回值  
 擷取的項目數目。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [VectorView Class](http://msdn.microsoft.com/zh-tw/79697692-ae58-40e0-958f-cf1be6347994)