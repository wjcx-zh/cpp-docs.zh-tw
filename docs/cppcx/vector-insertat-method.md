---
title: "Vector::InsertAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::InsertAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::InsertAt"
ms.assetid: 05b2ca08-234e-4fc0-acfd-cafa148d1577
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::InsertAt 方法
將指定的項目插入至目前 Vector 中，指定之索引所識別項目的後面。  
  
## 語法  
  
```  
  
virtual void InsertAt(  
   unsigned int index,   
   T item)  
```  
  
#### 參數  
 `index`  
 以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。  
  
 `item`  
 要插入至 Vector 中的項目，插入位置在 `index` 指定的項目後面。`item` 的類型是由 *T* typename 所定義。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)