---
title: "prev_permutation (STL/CLR) | Microsoft Docs"
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
  - "cliext::prev_permutation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "prev_permutation 函式 [STL/CLR]"
ms.assetid: 5294dbe5-1b5f-4369-a764-067dff86d1e8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# prev_permutation (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要重新排列範圍的項目，讓原始順序由詞傳統的下一個較大的範圍取代，如果有的話，其中明年五月感覺指定二進位述詞。  
  
## 語法  
  
```  
template<class _BidIt> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `prev_permutation` 相同。  如需詳細資訊，請參閱[prev\_permutation](../Topic/prev_permutation.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)