---
title: "remove_if (STL/CLR) | Microsoft Docs"
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
  - "cliext::remove_if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_if 函式 [STL/CLR]"
ms.assetid: de501d3f-965b-4a99-b833-f6fa303fbcdc
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# remove_if (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

排除符合從指定範圍的述詞，而不會干擾其他項目順序並傳回新範圍結尾沒有指定值的項目。  
  
## 語法  
  
```  
template<class _FwdIt, class _Pr> inline  
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `remove_if`。  如需詳細資訊，請參閱[remove\_if](../Topic/remove_if.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)