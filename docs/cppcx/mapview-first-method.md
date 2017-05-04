---
title: "MapView::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::First 方法"
ms.assetid: 9d7c7328-4f55-4ea6-a375-9d4e73707b56
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::First 方法
傳回指定對應檢視中之第一個項目的迭代器。  
  
## 語法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^   
First();  
```  
  
## 傳回值  
 迭代器，指定對應檢視中的第一個元素。  
  
## 備註  
 若要保留 First\(\) 所傳回的迭代器，為使用 [auto](~/cpp/auto-cpp.md) 型别推斷關鍵字進行宣告的變數指派傳回值，是很方便的方式。 例如，`auto x = myMapView->First();`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)