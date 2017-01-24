---
title: "slice 類別 | Microsoft Docs"
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
  - "valarray/std::slice"
  - "std.slice"
  - "slice"
  - "std::slice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "slice 類別"
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
caps.latest.revision: 23
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# slice 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

valarray 的一個公用程式類別，用來定義父代 valarray 的一維子集。  如果 valarray 被視為含有陣列中所有元素的二維矩陣，則配量會從二維陣列中擷取一維的向量。  
  
## 備註  
 此類別會儲存用來描述類型 [slice\_array](../standard-library/slice-array-class.md) 之物件的參數。當類別 slice 的物件作為類別 [valarray](../Topic/valarray::operator.md)**\<Type\>** 之物件的引數時，將會間接建構 valarray 的子集。  會指定從父 valarray 選取之子集的預存值包括：  
  
-   valarray 中的起始索引。  
  
-   總長度，或配量中的項目數。  
  
-   分散，或 valarray 中後續索引之間的距離。  
  
 如果配量定義的集合是常數 valarray 的子集，則配量會是新的 valarray。  如果配量定義的集合是非常數 valarray 的子集，則配量會有原始 valarray 的參考語意。  非常數 valarrays 的評估機制可節省時間和記憶體。  
  
 只有在配量所定義的來源和目的地子集相異，且所有索引皆有效時，才能保證 valarray 的作業。  
  
### 建構函式  
  
|||  
|-|-|  
|[配量](../Topic/slice::slice.md)|定義 `valarray` 的子集，其中包含等距且在指定項目開始的一些項目。|  
  
### 成員函式  
  
|||  
|-|-|  
|[大小](../Topic/slice::size.md)|尋找 `valarray` 之配量中的項目數。|  
|[start](../Topic/slice::start.md)|尋找 `valarray` 之配量的起始索引。|  
|[分散](../Topic/slice::stride.md)|尋找 `valarray` 之配量的元素之間的距離。|  
  
## 需求  
 **標頭：**\<valarray\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)