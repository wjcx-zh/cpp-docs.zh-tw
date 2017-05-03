---
title: "Vector::SetAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::SetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::SetAt"
ms.assetid: ddfb454e-dbfd-4831-b040-674b085d8fb6
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::SetAt 方法
在目前 Vector 中，將指定的值指派給由指定的索引所識別的元素。  
  
## 語法  
  
```  
  
virtual void SetAt(  
   unsigned int index,   
   T item  
);  
```  
  
#### 參數  
 `index`  
 以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。  
  
 `item`  
 要指派給指定項目的值。`item` 的類型是由 *T* typename 所定義。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)