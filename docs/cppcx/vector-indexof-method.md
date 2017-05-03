---
title: "Vector::IndexOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::IndexOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::IndexOf 方法"
ms.assetid: 4a965992-3858-4e3f-992a-b94c0580b2f7
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::IndexOf 方法
在目前 Vector 中搜尋指定的項目，如果找到，則傳回項目的索引。  
  
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
  
 如果該項目是 Vector 的第一項元素或找不到該項目，則 `index` 參數為 0。 如果傳回值為 `true`，表示找到符合項目，並且是第一個項目，否則表示找不到項目。  
  
## 傳回值  
 如果找到指定的項目則為 `true`，否則為 `false`。  
  
## 備註  
 IndexOf 使用 std::find\_if 尋找項目。 因此，自訂元素類型應多載 \=\= 和 \!\= 運算子，以啟用 find\_if 所需的等號比較。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)