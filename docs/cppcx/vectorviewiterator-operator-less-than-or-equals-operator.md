---
title: "VectorViewIterator::operator&lt;= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator<= 運算子"
ms.assetid: 523bf6ca-fb45-498b-8e94-fa8a093dd4ad
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&lt;= 運算子
指出目前 VectorIterator 是否小於或等於指定的 VectorIterator。  
  
## 語法  
  
```  
  
bool operator<=(  
   const VectorViewIterator& other  
) const;  
```  
  
#### 參數  
 `other`  
 另一個 VectorIterator。  
  
## 傳回值  
 如果目前的 VectorIterator 小於或等於 `other` 則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)