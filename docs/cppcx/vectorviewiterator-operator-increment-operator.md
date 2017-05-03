---
title: "VectorViewIterator::operator++ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator++ 運算子"
ms.assetid: 5391e6e2-a7ee-4dab-8cee-b2237894246f
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator++ 運算子
遞增目前 VectorViewIterator。  
  
## 語法  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(  
   int  
);  
```  
  
## 傳回值  
 第一種語法會先遞增再傳回目前 VectorViewIterator。 第二種語法會傳回目前 VectorViewIterator 的複本，然後遞增目前 VectorViewIterator。  
  
## 備註  
 第一種 VectorViewIterator 語法會前置遞增目前 VectorViewIterator。  
  
 第二種語法會後置遞增目前 VectorViewIterator。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)