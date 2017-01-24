---
title: "unique (STL/CLR) | Microsoft Docs"
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
  - "cliext::unique"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique 函式 [STL/CLR]"
ms.assetid: 833cc314-b452-4659-bbb4-575c2bb63855
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unique (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除是彼此相鄰中指定範圍內的重複的項目。  
  
## 語法  
  
```  
template<class _FwdIt> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `unique` 相同。  如需詳細資訊，請參閱[唯一](../Topic/unique%20\(%3Calgorithm%3E\).md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)