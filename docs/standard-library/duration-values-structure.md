---
title: "duration_values 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::duration_values"
dev_langs: 
  - "C++"
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# duration_values 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為 [期間](../standard-library/duration-class.md) 樣板參數 `Rep` 所提供的特定值。  
  
## 語法  
  
```  
template<class Rep>  
   struct duration_values;  
```  
  
## 成員  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[duration\_values::max 方法](../Topic/duration_values::max%20Method.md)|靜態。  為型別 `Rep` 值指定上限。|  
|[duration\_values::min 方法](../Topic/duration_values::min%20Method.md)|靜態。  為型別 `Rep` 值指定下限。|  
|[duration\_values::zero 方法](../Topic/duration_values::zero%20Method.md)|靜態。  傳回 `Rep(0)`。|  
  
## 需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)