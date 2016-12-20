---
title: "指標運算 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "算術指標"
  - "指標運算"
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 指標運算
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

加法類運算與指標相關，並且只有當指標運算元定址陣列成員且整數值在同一個陣列的界限內產生位移時，整數才會提供有意義的結果。  將整數值轉換為位址位移時，編譯器會假設原始位址和位址加上位移之間只有相同大小的記憶體位置。  
  
 這個假設對陣列成員有效。  根據定義，陣列是一系列相同類型的值；其元素位於連續的記憶體位置。  不過，除了陣列元素外，不保證相同類型的識別項會填滿任何類型的儲存區。  也就是說，即使是相同類型的位置，記憶體位置之間也可能會出現空白。  因此，在陣列元素以外的任何位址加入或減去入值，都會出現未定義的結果。  
  
 同樣地，減去兩個指標值時，轉換會假設運算元指定的位址之間只有相同類型的值，而沒有空白。  
  
## 請參閱  
 [C 加法類運算子](../c-language/c-additive-operators.md)