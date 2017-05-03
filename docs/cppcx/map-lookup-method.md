---
title: "Map::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Lookup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Lookup 方法"
ms.assetid: c56773ae-2df0-4d21-a6ab-9603529547b0
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Lookup 方法
取得與類型為 K 之指定機碼 \(如果該機碼存在的話\) 相關聯且類型為 V 的值。  
  
## 語法  
  
```  
V Lookup(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來在 Map 中尋找元素的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 與 `key` 配對的值。 傳回值的類型為 typename *V*。  
  
## 備註  
 如果機碼不存在，則會擲回 [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md)。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)