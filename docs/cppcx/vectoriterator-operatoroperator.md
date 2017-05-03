---
title: "VectorIterator::operatorOperator | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator[] 運算子"
ms.assetid: e1ba8101-8c16-4be1-b31b-91099d6e81f3
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operatorOperator
擷取從目前 VectorIterator 開始指定偏移的元素的參考。  
  
## 語法  
  
```  
  
reference operator[](difference_type n) const;  
```  
  
#### 參數  
 `n`  
 整數位移。  
  
## 傳回值  
 從目前 VectorIterator 偏移 `n` 個元素的元素。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)