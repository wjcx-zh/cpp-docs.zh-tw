---
title: "BackInsertIterator::operator* 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::operator*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::operator* 運算子"
ms.assetid: 68d70bc8-da84-49c6-ba35-4ac5aa6dad16
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::operator* 運算子
擷取目前 BackInsertIterator 的參考。  
  
## 語法  
  
```  
BackInsertIterator& operator*();  
```  
  
## 傳回值  
 目前 BackInsertIterator 的參考。  
  
## 備註  
 這個運算子會傳回目前 BackInsertIterator 的參考，不是目前集合中任何項目的參考。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::BackInsertIterator 類別](../cppcx/platform-collections-backinsertiterator-class.md)