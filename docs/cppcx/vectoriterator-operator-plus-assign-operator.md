---
title: "VectorIterator::operator+= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator+="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator+= 運算子"
ms.assetid: 9fd0d8a9-29ae-439a-b6ee-39e8fcf225ec
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator+= 運算子
依指定的位移值遞增目前 VectorIterator。  
  
## 語法  
  
```  
VectorIterator& operator+=(  
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
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)