---
title: "MapView::Lookup 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::Lookup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::Lookup 方法"
ms.assetid: 93090ac3-3f1d-4b7e-b80e-164b8c65cd29
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::Lookup 方法
取得與類型為 K 之指定機碼相關聯且類型為 V 的值。  
  
## 語法  
  
```  
V Lookup(  
   K key  
);  
```  
  
#### 參數  
 `key`  
 用來在 MapView 中尋找元素的機碼。`key` 的類型為 typename *K*。  
  
## 傳回值  
 與 `key` 配對的值。 傳回值的類型為 typename *V*。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)