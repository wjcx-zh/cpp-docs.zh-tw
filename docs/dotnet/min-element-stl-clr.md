---
title: "min_element (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::min_element"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "min_element 函式 [STL/CLR]"
ms.assetid: 2a9c6828-9722-454f-9c10-d4a184d4d21b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# min_element (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在指定的範圍內尋找第一個最小項目，其中順序準則可由二元述詞指定。  
  
## 語法  
  
```  
template<class _FwdIt> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## 備註  
 這個函式的運作和STL函式一樣`min_element`.  如需詳細資訊，請參閱[min\_element](../Topic/min_element.md)。  
  
## 需求  
 **Header:** \<cliext\/algorithm\>  
  
 **Namespace:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)