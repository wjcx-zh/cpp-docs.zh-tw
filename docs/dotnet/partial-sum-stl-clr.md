---
title: "partial_sum (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::partial_sum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partial_sum 函式 [STL/CLR]"
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# partial_sum (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

透過 `i`th 項目在 `i`目的範圍的 th 項目計算輸入範圍的一系列的總和從第一個項目並儲存每個這類總和的結果或計算總和作業由另一個指定的二進位運算取代通用程序的結果。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## 備註  
 這個函式的行為與 STL 數值函式 `partial_sum` 相同。  如需詳細資訊，請參閱[partial\_sum](../Topic/partial_sum.md)。  
  
## 需求  
 **標頭：** \<cliext\/numeric\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [數值](../dotnet/numeric-stl-clr.md)