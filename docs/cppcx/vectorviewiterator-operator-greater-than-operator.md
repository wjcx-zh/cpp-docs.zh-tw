---
title: "VectorViewIterator::operator&gt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator> 運算子"
ms.assetid: c689b677-e3c6-4f6e-8e3a-54d5f2a6123d
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&gt; 運算子
指出目前 VectorViewIterator 是否大於指定的 VectorViewIterator。  
  
## 語法  
  
```  
  
bool operator>(  
   const VectorViewIterator& other  
) const;  
```  
  
#### 參數  
 `other`  
 另一個 VectorViewIterator。  
  
## 傳回值  
 如果目前 VectorViewIterator 大於 `true` 則為 `other`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)