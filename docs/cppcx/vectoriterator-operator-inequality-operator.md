---
title: "VectorIterator::operator!= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator!= 運算子"
ms.assetid: 88b71c7e-9c88-4282-a518-455059da16c2
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator!= 運算子
指出目前 VectorIterator 是否不等於指定的 VectorIterator。  
  
## 語法  
  
```  
bool operator!=(  
   const VectorIterator& other  
) const;  
```  
  
#### 參數  
 `other`  
 另一個 VectorIterator。  
  
## 傳回值  
 如果目前的 VectorIterator 不等於 `other` 則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)