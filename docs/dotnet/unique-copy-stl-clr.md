---
title: "unique_copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::unique_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique_copy 函式 [STL/CLR]"
ms.assetid: 37aa5b06-42c5-420d-94c5-00f00ad26471
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unique_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將來源範圍的項目複製到目的範圍 \(除了是彼此相鄰的重複項目\)。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `unique_copy` 相同。  如需詳細資訊，請參閱[unique\_copy](../Topic/unique_copy.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)