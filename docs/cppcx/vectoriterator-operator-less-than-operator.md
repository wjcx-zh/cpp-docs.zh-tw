---
title: "VectorIterator::operator&lt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator< 運算子"
ms.assetid: 1d7dabdd-70da-4c39-b76e-e22e743751a0
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator&lt; 運算子
指出目前 VectorIterator 是否小於指定的 VectorIterator。  
  
## 語法  
  
```cpp  
  
bool operator<(  
   const VectorIterator& other  
) const   
```  
  
#### 參數  
 `other`  
 另一個 VectorIterator。  
  
## 傳回值  
 如果目前 VectorIterator 小於 `true` 則為 `other`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)