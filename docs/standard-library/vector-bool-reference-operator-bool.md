---
title: "vector&lt;bool&gt;::reference::operator bool | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "operatorbool"
  - "vector<bool>::reference::operatorbool"
  - "bool"
  - "std::vector<bool>::reference::operatorbool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL 運算子"
  - "reference::operator bool"
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# vector&lt;bool&gt;::reference::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供從 `vector<bool>::reference` 至 `bool` 的隱含轉換。  
  
## 語法  
  
```  
operator bool( ) const;  
```  
  
## 傳回值  
 [vector\<bool\>](../standard-library/vector-bool-class.md) 物件項目的布林值。  
  
## 備註  
 這個運算子無法修改 `vector<bool>` 物件。  
  
## 需求  
 **標頭：**\<vector\>  
  
 **命名空間:** std  
  
## 請參閱  
 [vector\<bool\>::reference 類別](../standard-library/vector-bool-reference-class.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)