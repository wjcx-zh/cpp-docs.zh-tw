---
title: "BackInsertIterator::operator++ 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::operator++ 運算子"
ms.assetid: 08324574-db2b-4d95-825e-a93a56f327da
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::operator++ 運算子
傳回目前 BackInsertIterator 的參考。 迭代器是未修改的。  
  
## 語法  
  
```  
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(  
   int  
);  
```  
  
## 傳回值  
 目前 BackInsertIterator 的參考。  
  
## 備註  
 根據設計，第一個語法範例會對目前 BackInsertIterator 前置遞增，而第二個語法則是對目前 BackInsertIterator 後置遞增。 第二個語法中的 `int` 類型代表後置遞增作業，而不是實際的整數運算元。  
  
 不過，這個運算子不會實際修改 BackInsertIterator。 而是傳回未修改之目前迭代器的參考。 這項行為與 [operator\*](../cppcx/backinsertiterator-operator-dereference-operator.md) 相同。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::BackInsertIterator 類別](../cppcx/platform-collections-backinsertiterator-class.md)