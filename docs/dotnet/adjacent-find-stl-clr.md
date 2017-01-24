---
title: "adjacent_find (STL/CLR) | Microsoft Docs"
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
  - "cliext::adjacent_find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adjacent_find 函式"
ms.assetid: 48bf57ea-b128-4d16-97c5-01d8a378369f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# adjacent_find (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

搜尋是等於或符合指定之條件的兩個相鄰的項目。  
  
## 語法  
  
```  
template<class _FwdIt> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `adjacent_find` 相同。  如需詳細資訊，請參閱[adjacent\_find](../Topic/adjacent_find.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)