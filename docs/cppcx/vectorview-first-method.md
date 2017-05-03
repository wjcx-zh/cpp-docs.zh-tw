---
title: "VectorView::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::First 方法"
ms.assetid: 543a5c5b-8ce3-4be3-9fad-726928de7855
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::First 方法
傳回迭代器，指定 VectorView 中的第一個項目。  
  
## 語法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
## 傳回值  
 指定 VectorView 中第一個項目的迭代器。  
  
## 備註  
 若要保留 First\(\) 所傳回的迭代器，為使用 [auto](../Topic/auto%20\(C++\).md) 型别推斷關鍵字進行宣告的變數指派傳回值，是很方便的方式。 例如，`auto x = myVectorView->First();`。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [VectorView Class](http://msdn.microsoft.com/zh-tw/79697692-ae58-40e0-958f-cf1be6347994)