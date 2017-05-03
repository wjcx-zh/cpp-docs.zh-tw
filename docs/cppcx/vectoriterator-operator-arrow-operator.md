---
title: "VectorIterator::operator-&gt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator-> 運算子"
ms.assetid: d6caed5c-4899-45f8-95a2-687eafeeb8e1
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator-&gt; 運算子
擷取目前 VectorIterator 參考的元素的位址。  
  
## 語法  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
## 傳回值  
 目前 VectorIterator 參考的項目值。  
  
 傳回值的類型是實作這個運算子所需之未指定的內部類型。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)