---
title: "VectorIterator::operator-- 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator--"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator-- 運算子"
ms.assetid: 650a3037-2984-4110-9d7c-cd3756e5f4b9
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator-- 運算子
遞減目前 VectorIterator。  
  
## 語法  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(  
   int  
);  
```  
  
## 傳回值  
 第一種語法會先遞減，再傳回目前的 VectorIterator。 第二種語法先傳回目前 VectorIterator 的複本，再遞減目前的 VectorIterator。  
  
## 備註  
 第一種 VectorIterator 語法會預先遞減目前的 VectorIterator。  
  
 第二種語法會後置遞減目前的 VectorIterator。 第二種語法中的 `int` 類型表示後置遞減作業，不是實際的整數運算元。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)