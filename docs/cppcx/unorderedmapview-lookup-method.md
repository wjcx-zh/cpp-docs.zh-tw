---
title: "UnorderedMapView::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::Lookup"
ms.assetid: 22f61824-ba8c-4b8c-9077-7577c41a6742
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::Lookup 方法
取得與類型為 K 之指定機碼相關聯且類型為 V 的值。  
  
## 語法  
  
```cpp  
V Lookup(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來在 UnorderedMapView 中尋找元素的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 與 `key` 配對的值。 傳回值的類型為 typename *V*。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)