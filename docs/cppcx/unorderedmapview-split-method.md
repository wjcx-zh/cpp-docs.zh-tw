---
title: "UnorderedMapView::Split 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::Split"
ms.assetid: b759d254-40c9-40f1-9838-106ffb2c5626
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::Split 方法
將目前 UnorderedMapView 物件分割為兩個 UnorderedMapView 物件。 這個方法無法操作。  
  
## 語法  
  
```cpp  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K,  
                         V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K,  
                         V>^ * secondPartition  
);  
```  
  
#### 參數  
 `firstPartition`  
 原始 UnorderedMapView 物件的第一個部分。  
  
 `secondPartition`  
 原始 UnorderedMapView 物件的第二個部分。  
  
## 備註  
 這個方法無法操作，不會執行任何動作。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::UnorderedMapView 類別](../cppcx/platform-collections-unorderedmapview-class.md)