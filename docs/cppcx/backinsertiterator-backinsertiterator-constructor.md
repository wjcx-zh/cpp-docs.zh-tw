---
title: "BackInsertIterator::BackInsertIterator 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::BackInsertIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::BackInsertIterator 建構函式"
ms.assetid: ae6f0213-a7bb-43b8-9a5e-7a8dad7c76f8
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::BackInsertIterator 建構函式
初始化 `BackInsertIterator` 類別的新執行個體。  
  
## 語法  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v  
);  
```  
  
#### 參數  
 `v`  
 IVector\<T\> 物件。  
  
## 備註  
 `BackInsertIterator` 在參數 `v` 所指定的物件的最後一個元素之後插入元素。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::BackInsertIterator 類別](../cppcx/platform-collections-backinsertiterator-class.md)