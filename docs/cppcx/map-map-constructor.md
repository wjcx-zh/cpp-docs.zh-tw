---
title: "Map::Map 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Map 建構函式"
ms.assetid: 4cd314eb-e3e3-4fa7-8c58-96e48d167246
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Map 建構函式
初始化 Map 類別的新執行個體。  
  
## 語法  
  
```  
explicit Map(  
   const C& comp = C()  
);  
explicit Map(  
   const StdMap& m  
);  
explicit Map(  
   StdMap&& m  
);  
template <  
   typename InIt  
>  
Map(  
   InItfirst,  
   InItlast,  
   const C& comp = C()  
);  
```  
  
#### 參數  
 `InIt`  
 目前 Map 的 typename。  
  
 `comp`  
 一個型別，提供函式物件，可以根據排序鍵比較兩個項目值，判斷它們在 Map 中的相對順序。  
  
 `m`  
 用來初始化目前 Map 之 [Lvalues 和 Rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md) 的參考或 [map 類別](../standard-library/map-class.md)。  
  
 `first`  
 用來初始化目前 Map 的項目範圍中，第一個項目的輸入迭代器。  
  
 `last`  
 用來初始化目前 Map 的項目範圍以外第一個項目的輸入迭代器。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)