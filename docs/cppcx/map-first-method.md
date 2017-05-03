---
title: "Map::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::First 方法"
ms.assetid: bb1a4458-ecc3-43b0-b808-1693f853ad82
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::First 方法
傳回指定 Map 中第一個元素的迭代器。如果 Map 是空的，則傳回 `nullptr`。  
  
## 語法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
## 傳回值  
 迭代器，指定對應中的第一個元素。  
  
## 備註  
 若要保留 First\(\) 所傳回的迭代器，為使用 [auto](../Topic/auto%20\(C++\).md) 型别推斷關鍵字進行宣告的變數指派傳回值，是很方便的方式。 例如，`auto x = myMap->First();`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)