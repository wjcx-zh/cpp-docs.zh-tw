---
title: "InputIterator::operator== 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator::operator== 運算子"
ms.assetid: 84f1b69a-77b9-467c-ad1a-2fe8a7c3009e
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# InputIterator::operator== 運算子
指出目前 InputIterator 是否等於指定的 InputIterator。  
  
## 語法  
  
```  
bool operator==(  
   const InputIterator& other  
) const;  
```  
  
#### 參數  
 `other`  
 另一個 InputIterator。  
  
## 傳回值  
 如果目前 InputIterator 等於 `true` 則為 `other`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::InputIterator 類別](../cppcx/platform-collections-inputiterator-class.md)