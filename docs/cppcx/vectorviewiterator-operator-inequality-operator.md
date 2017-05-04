---
title: "VectorViewIterator::operator!= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator!= 運算子"
ms.assetid: 00d55da7-9d85-495b-baaa-b5cdfa81aa7d
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator!= 運算子
指出目前 VectorViewIterator 是否不等於指定的 VectorViewIterator。  
  
## 語法  
  
```  
bool operator!=(  
   const VectorViewIterator& other  
) const;  
```  
  
#### 參數  
 `other`  
 另一個 VectorViewIterator。  
  
## 傳回值  
 如果目前的 VectorViewIterator 不等於 `other` 則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)