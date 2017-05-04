---
title: "BackInsertIterator::operator= 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::operator= 運算子"
ms.assetid: 509c9b4c-14fb-4318-bf65-b8926cc72f4f
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::operator= 運算子
將指定的物件附加至目前循序集合的結尾。  
  
## 語法  
  
```  
  
BackInsertIterator& operator=(  
   const T& t  
);  
```  
  
#### 參數  
 `t`  
 要附加至目前集合的物件。  
  
## 傳回值  
 目前 BackInsertIterator 的參考。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::BackInsertIterator 類別](../cppcx/platform-collections-backinsertiterator-class.md)