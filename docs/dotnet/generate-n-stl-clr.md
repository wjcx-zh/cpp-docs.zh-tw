---
title: "generate_n (STL/CLR) | Microsoft Docs"
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
  - "cliext::generate_n"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generate_n 函式 [STL/CLR]"
ms.assetid: 2f56e649-7a6f-4861-ae49-d0b25f5cd50c
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# generate_n (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指派給項目的指定數目的函式物件產生的值是範圍並返回到最後指定值的位置。  
  
## 語法  
  
```  
template<class _OutIt, class _Diff, class _Fn0> inline  
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `generate_n` 相同。  如需詳細資訊，請參閱[generate\_n](../Topic/generate_n.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)