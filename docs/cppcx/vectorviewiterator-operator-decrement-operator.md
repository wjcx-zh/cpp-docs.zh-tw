---
title: "VectorViewIterator::operator-- 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator--"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator-- 運算子"
ms.assetid: edf3ba42-1fa4-4795-9a37-1f7dfb23ad19
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator-- 運算子
遞減目前 VectorViewIterator。  
  
## 語法  
  
```  
VectorViewIterator& operator--();  
VectorViewIterator operator--(  
   int  
);  
```  
  
## 傳回值  
 第一種語法會先遞減再傳回目前 VectorViewIterator。 第二種語法會傳回目前 VectorViewIterator 的複本，然後遞減目前 VectorViewIterator。  
  
## 備註  
 第一種 VectorViewIterator 語法會前置遞減目前 VectorViewIterator。  
  
 第二種語法會後置遞減目前 VectorViewIterator。 第二種語法中的 `int` 類型表示後置遞減作業，不是實際的整數運算元。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)