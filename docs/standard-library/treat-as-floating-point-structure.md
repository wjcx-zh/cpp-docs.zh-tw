---
title: "treat_as_floating_point 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::treat_as_floating_point"
dev_langs: 
  - "C++"
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# treat_as_floating_point 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 `Rep` 是否可以將浮點型別。  
  
## 語法  
  
```  
template<class Rep>  
struct treat_as_floating_point : is_floating_point<Rep>;  
```  
  
## 備註  
 ，只有在特製化 `treat_as_floating_point<Rep>` 從 [true\_type](../Topic/true_type%20Typedef.md)時，取得`Rep` 可以視為一個浮點型別。  樣板類別可以提供使用者定義型別特製化。  
  
## 需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)