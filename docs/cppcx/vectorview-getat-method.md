---
title: "VectorView::GetAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::GetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::GetAt 方法"
ms.assetid: 01c5feda-2a97-4429-ae15-4aced96ce332
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::GetAt 方法
擷取由指定之索引所表示的目前 VectorView 項目。  
  
## 語法  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
#### 參數  
 `index`  
 以零起始、不帶正負號的整數，在 VectorView 物件中指定特別項目。  
  
## 傳回值  
 `index` 參數指定的項目。 VectorView 範本參數指定的項目類型，*T*。  
  
## 需求  
 **標頭：**collection.h  
  
 **命名空間：**Platform::Collections  
  
## 請參閱  
 [VectorView Class](http://msdn.microsoft.com/zh-tw/79697692-ae58-40e0-958f-cf1be6347994)