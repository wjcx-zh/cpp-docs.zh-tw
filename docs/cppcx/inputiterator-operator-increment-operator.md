---
title: "InputIterator::operator++ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator::operator++ 運算子"
ms.assetid: 50781585-7a12-4f02-bff8-68fe0adf0693
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# InputIterator::operator++ 運算子
遞增目前 InputIterator。  
  
## 語法  
  
```  
  
InputIterator& operator++();  
  
InputIterator operator++(  
   int  
);  
```  
  
## 傳回值  
 第一種語法會先遞增再傳回目前 InputIterator。 第二種語法會傳回目前 InputIterator 的複本，然後遞增目前 InputIterator。  
  
## 備註  
 第一種 InputIterator 語法會前置遞增目前 InputIterator。  
  
 第二種語法會後置遞增目前 InputIterator。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::InputIterator 類別](../cppcx/platform-collections-inputiterator-class.md)