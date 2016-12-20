---
title: "fill_n (STL/CLR) | Microsoft Docs"
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
  - "cliext::fill_n"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fill_n 函式"
ms.assetid: bb9f2f71-ba1d-44ec-8b47-6ece149dd6b8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# fill_n (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指派新值給以特定項目開頭之範圍中的指定項目數。  
  
## 語法  
  
```  
template<class _OutIt, class _Diff, class _Ty> inline  
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `fill_n`。  如需詳細資訊，請參閱[fill\_n](../Topic/fill_n.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)