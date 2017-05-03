---
title: "VectorView::IndexOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::IndexOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::IndexOf 方法"
ms.assetid: 848117ec-ad4a-4a0b-9c1e-9076e5188869
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::IndexOf 方法
在目前 VectorView 中搜尋指定的項目，如果找到，則傳回項目的索引。  
  
## 語法  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
#### 參數  
 `value`  
 要尋找的項目。  
  
 `index`  
 如果找到參數 `value`，則為項目以零起始的索引，否則為 0。  
  
 如果項目是 VectorView 的第一個項目或找不到項目，則 `index` 參數為 0。 如果傳回值為 `true`，表示找到符合項目，並且是第一個項目，否則表示找不到項目。  
  
## 傳回值  
 如果找到指定的項目則為 `true`，否則為 `false`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [VectorView Class](http://msdn.microsoft.com/zh-tw/79697692-ae58-40e0-958f-cf1be6347994)