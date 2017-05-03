---
title: "Map::GetView 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::GetView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::GetView 方法"
ms.assetid: d432bb98-d354-4caa-8c2b-794406ac0b0b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::GetView 方法
傳回目前 Map 的唯讀檢視 \(也就是 [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)\)，它會實作 [Windows::Foundation::Collections::IMapView\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) 介面。  
  
## 語法  
  
```  
  
Windows::Foundation::Collections::IMapView<K, V>^   
   GetView();  
```  
  
## 傳回值  
 `MapView` 物件。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)   
 [Platform::Collections::UnorderedMapClass](../cppcx/platform-collections-unorderedmap-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)