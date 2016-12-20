---
title: "iter_swap (STL/CLR) | Microsoft Docs"
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
  - "cliext::iter_swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iter_swap 函式 [STL/CLR]"
ms.assetid: 9809c9f5-2ca6-4e9e-97c1-d7973d3134f8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# iter_swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交換兩個值由一組指定之 Iterator 所參考的。  
  
## 語法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `iter_swap` 相同。  如需詳細資訊，請參閱[iter\_swap](../Topic/iter_swap.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)