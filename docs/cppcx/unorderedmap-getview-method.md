---
title: "UnorderedMap::GetView 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::GetView"
ms.assetid: 41a12802-3f42-461c-a6fc-a35fc34517f2
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::GetView 方法
傳回目前 UnorderedMap 的唯讀檢視 \(也就是 [Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)\)，它會實作 [Windows::Foundation::Collections::IMapView::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) 介面。  
  
## 語法  
  
```scr  
  
Windows::Foundation::Collections::IMapView<K, V>^   
   GetView();  
```  
  
## 傳回值  
 `UnorderedMapView` 物件。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [集合](../cppcx/collections-c-cx.md)   
 [Platform::Collections::UnorderedMap 類別](../cppcx/platform-collections-unorderedmap-class.md)   
 [Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)