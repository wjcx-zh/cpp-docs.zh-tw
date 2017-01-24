---
title: "swap_ranges (STL/CLR) | Microsoft Docs"
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
  - "cliext::swap_ranges"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap_ranges 函式 [STL/CLR]"
ms.assetid: 3fb39a84-b088-48f1-8bb7-2bbe68b048a9
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# swap_ranges (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

與另一個相同大小的範圍交換項目。  
  
## 語法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,  
        _FwdIt2 _First2);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `swap_ranges` 相同。  如需詳細資訊，請參閱[swap\_ranges](../Topic/swap_ranges.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)