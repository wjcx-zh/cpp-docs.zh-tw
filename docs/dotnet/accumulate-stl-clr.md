---
title: "accumulate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::accumulate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accumulate 函式 [STL/CLR]"
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# accumulate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

透過計算執行部分和計算所有項目的總和在指定的範圍加入一些初始值或計算使用指定的二進位運算的方式取得執行部分結果的總和之外。  
  
## 語法  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 數字函式的 `accumulate`。  如需詳細資訊，請參閱[accumulate](../Topic/accumulate.md)。  
  
## 需求  
 **標題:** \<cliext\/數值\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [數值](../dotnet/numeric-stl-clr.md)