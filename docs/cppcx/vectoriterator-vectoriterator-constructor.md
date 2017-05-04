---
title: "VectorIterator::VectorIterator 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::VectorIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::VectorIterator 建構函式"
ms.assetid: 93286731-9499-4bfb-a24b-b302479c38cc
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::VectorIterator 建構函式
初始化 VectorIterator 類別的新執行個體。  
  
## 語法  
  
```  
  
VectorIterator();  
  
explicit VectorIterator(  
   Windows::Foundation::Collections::IVector<T>^ v  
);  
```  
  
#### 參數  
 `v`  
 IVector\<T\> 物件。  
  
## 備註  
 第一個語法範例是預設建構函式。 第二個語法範例是明確建構函式，用來從 IVector\<T\> 物件建構 VectorIterator。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)