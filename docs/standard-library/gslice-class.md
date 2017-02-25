---
title: "gslice 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::gslice"
  - "std.gslice"
  - "gslice"
  - "valarray/std::gslice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gslice 類別"
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# gslice 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

valarray 的一個公用程式類別，用來定義 valarray 的多維度子集。  如果 valarray 被視為含有陣列中所有元素的多維度矩陣，則配量會從多維度陣列中擷取向量。  
  
## 備註  
 此類別會儲存用來描述類型 [gslice\_array](../standard-library/gslice-array-class.md) 之物件的參數。  當類別 gslice 的物件作為類別 [valarray](../Topic/valarray::operator.md)**\<Type\>** 之物件的引數時，將會間接建構 valarray 的子集。  會指定從父 valarray 選取之子集的預存值包括：  
  
-   起始索引。  
  
-   類別 **valarray\<size\_t\>** 的長度向量。  
  
-   類別 **valarray\<size\_t\>** 的分散向量。  
  
 兩個向量的長度必須相同。  
  
 如果 gslice 定義的集合是常數 valarray 的子集，則 gslice 會是新的 valarray。  如果 gslice 定義的集合是非常數 valarray 的子集，則 gslice 會有原始 valarray 的參考語意。  非常數 valarrays 的評估機制可節省時間和記憶體。  
  
 只有在 gslice 所定義的來源和目的地子集相異，且所有索引皆有效時，才能保證 valarray 的作業。  
  
### 建構函式  
  
|||  
|-|-|  
|[gslice](../Topic/gslice::gslice.md)|定義 `valarray` 的子集，其中包含 `valarray` 的多個配量 \(全都起始於指定的元素\)。|  
  
### 成員函式  
  
|||  
|-|-|  
|[大小](../Topic/gslice::size.md)|尋找指定 `valarray` 之一般配量中的元素數的陣列值。|  
|[start](../Topic/gslice::start.md)|尋找 `valarray` 之一般配量的起始索引。|  
|[分散](../Topic/gslice::stride.md)|尋找 `valarray` 之一般配量的元素之間的距離。|  
  
## 需求  
 **標頭：**\<valarray\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)