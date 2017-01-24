---
title: "nth_element (STL/CLR) | Microsoft Docs"
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
  - "cliext::nth_element"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nth_element 函式 [STL/CLR]"
ms.assetid: 19fc1695-62a9-4f85-9920-d153c1c6481f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nth_element (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

分割正確設定序列的 `n`th 項目範圍範圍，以便在它前面的所有項目小於或等於，而且後面序列中的所有項目大於或等於它。  
  
## 語法  
  
```  
template<class _RanIt> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,  
        _Pr _Pred);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `nth_element` 相同。  如需詳細資訊，請參閱[nth\_element](../Topic/nth_element.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)