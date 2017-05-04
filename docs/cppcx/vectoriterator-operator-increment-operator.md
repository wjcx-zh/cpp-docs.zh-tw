---
title: "VectorIterator::operator++ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator++ 運算子"
ms.assetid: c46b18ff-45be-436a-8f31-b3a5ecc19b77
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator++ 運算子
遞增目前 VectorIterator。  
  
## 語法  
  
```  
  
VectorIterator& operator++();  
VectorIterator operator++(  
   int  
);  
```  
  
## 傳回值  
 第一種語法會先遞增再傳回目前 VectorIterator。 第二種語法傳回目前 VectorIterator 的複本，然後遞增目前 VectorIterator。  
  
## 備註  
 第一種 VectorIterator 語法會預先遞增目前 VectorIterator。  
  
 第二種語法會事後遞增目前 VectorIterator。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)