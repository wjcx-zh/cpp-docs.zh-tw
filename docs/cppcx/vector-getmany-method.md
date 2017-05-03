---
title: "Vector::GetMany 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetMany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetMany 方法"
ms.assetid: e2d5ccf4-101a-47e5-a0d8-56f65a7ff28d
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetMany 方法
從目前的 Vector 中，從指定的索引處開始，擷取一連串的項目，並將其複製到呼叫端配置的陣列中。  
  
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
 呼叫端配置的項目陣列，從 `startIndex` 指定的元素開始，並在 Vector 中的最後一個元素結束。  
  
## 傳回值  
 擷取的項目數目。  
  
## 備註  
 此函式並非直接供用戶端程式碼使用。 其用於 [to\_vector 函式](../cppcx/to-vector-function.md)內部，可有效率地將 Platform::Vector 執行個體轉換成 std::vector 執行個體。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)