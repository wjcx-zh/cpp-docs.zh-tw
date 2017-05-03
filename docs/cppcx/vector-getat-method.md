---
title: "Vector::GetAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetAt 方法"
ms.assetid: 3766b399-cef2-4006-9a87-50f717390cac
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetAt 方法
擷取由指定之索引所識別的目前 Vector 項目。  
  
## 語法  
  
```  
  
virtual T GetAt(  
   unsigned int index  
);  
```  
  
#### 參數  
 `index`  
 以零起始、不帶正負號的整數，在 Vector 物件中指定特別項目。  
  
## 傳回值  
 `index` 參數指定的項目。 項目類型是由 *T* typename 所定義。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)