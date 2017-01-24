---
title: "註標運算子的解譯 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 註標"
  - "解譯註標運算子"
  - "運算子 [C++], 註標的解譯"
  - "註標運算子, 的解譯"
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 註標運算子的解譯
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

註標運算子 \(**\[ \]**\) 就如同其他運算子一樣，可由使用者重新加以定義。  註標運算子的預設行為 \(如果未多載\) 是使用下列方法結合陣列名稱和註標：  
  
 \*\(\(*array\-name*\) \+ \(*subscript*\)\)  
  
 在包含指標類型的所有加法運算中，都會自動執行縮放來調整類型的大小。  因此，結果值不會是 *array\-name* 原點的 *subscript* 位元組，而是陣列的第 *subscript* 個元素。\(如需這項轉換的詳細資訊，請參閱[加法類運算子](../cpp/additive-operators-plus-and.md)\)。  
  
 同樣地，對於多維陣列而言，位址是使用下列方法衍生：  
  
 **\(\(**   
 ***array\-name* \) \+ \(**   
 ***subscript* 1**  *max*2 *\* max*3*...max*n\)               **\+** *subscript*2 *\* max*3*...max*n\)                    . . .  *\+* *subscript*n\)\)  
  
## 請參閱  
 [陣列](../cpp/arrays-cpp.md)