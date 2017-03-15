---
title: "adjacent_difference (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adjacent_difference 函式"
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# adjacent_difference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計算每個項目及其前置項之間執行區分輸入範圍並將結果輸出至目的範圍或計算差異作業由另一個取代通用程序，指定的二進位運算的結果。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## 備註  
 這個函式的行為與 STL 數值函式 `adjacent_difference` 相同。  如需詳細資訊，請參閱[adjacent\_difference](../Topic/adjacent_difference.md)。  
  
## 需求  
 **標頭：** \<cliext\/numeric\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [數值](../dotnet/numeric-stl-clr.md)