---
title: "Vector::Append 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::Append"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::Append"
ms.assetid: 877127c3-c7ce-4462-a240-5615fd582653
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::Append 方法
在目前 Vector 的最後一個項目之後插入指定的項目。  
  
## 語法  
  
```  
  
virtual void Append(  
   T item  
);  
```  
  
#### 參數  
 `index`  
 要插入 Vector 中的項目。`item` 的類型是由 *T* typename 所定義。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)