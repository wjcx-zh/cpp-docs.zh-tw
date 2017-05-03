---
title: "Array::get 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array::get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Array::get 方法"
ms.assetid: 3bbcd829-35e7-4912-99ba-6ab9de407287
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Array::get 方法
在指定的索引位置擷取對陣列元素的參考。  
  
## 語法  
  
```  
  
T& get(  
unsigned int index  
)  const;  
```  
  
#### 參數  
 `index`  
 識別陣列中元素的以零起始索引。 最小的索引是 0，而最大的索引是[陣列建構函式](../cppcx/array-constructors.md)中 `size` 參數所指定的值。  
  
## 傳回值  
 `index` 參數所指定的陣列元素。  
  
## 需求  
 **標頭：**vccorlib.h  
  
 **命名空間：**Platform  
  
## 請參閱  
 [Platform::Array 類別](../cppcx/platform-array-class.md)