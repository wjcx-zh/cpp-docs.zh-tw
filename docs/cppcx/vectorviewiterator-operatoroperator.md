---
title: "VectorViewIterator::operatorOperator | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator[] 運算子"
ms.assetid: 41bf327d-2037-457c-83df-6338fc1abbc2
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operatorOperator
擷取從目前 VectorViewIterator 開始指定位移之項目的參考。  
  
## 語法  
  
```  
reference operator[](difference_type n) const;  
```  
  
#### 參數  
 `n`  
 整數位移。  
  
## 傳回值  
 從目前 VectorViewIterator 位移 `n` 個項目的項目。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)