---
title: "rotate_copy (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::rotate_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rotate_copy 函式 [STL/CLR]"
ms.assetid: ed697552-130f-474f-9ab6-133332bb2587
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# rotate_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在兩個相鄰範圍內的元素指定來源並複製結果到目的範圍。  
  
## 語法  
  
```  
template<class _FwdIt, class _OutIt> inline  
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,  
        _OutIt _Dest);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `rotate_copy`。  如需詳細資訊，請參閱[rotate\_copy](../Topic/rotate_copy.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)