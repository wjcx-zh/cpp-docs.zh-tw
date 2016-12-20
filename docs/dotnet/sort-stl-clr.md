---
title: "sort (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::sort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sort 函式 [STL/CLR]"
ms.assetid: e30f3e97-60c4-4a8e-89f1-75ec056f587a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sort (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示在指定範圍內的元素載入至 nondescending 的命令或以二進位述詞指定的排序準則。  
  
## 語法  
  
```  
template<class _RanIt> inline  
    void sort(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `sort`。  如需詳細資訊，請參閱[排序](../Topic/sort.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)