---
title: "VectorViewIterator::operator-= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator-="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator-= 運算子"
ms.assetid: fc4d5f19-a001-44fd-aabe-972d8b54ca2f
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator-= 運算子
依指定的位移遞減目前 VectorIterator。  
  
## 語法  
  
```  
VectorViewIterator& operator-=(  
   difference_type n  
);  
```  
  
#### 參數  
 `n`  
 整數位移。  
  
## 傳回值  
 更新後的 VectorIterator。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)