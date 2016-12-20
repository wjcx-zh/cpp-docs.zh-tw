---
title: "transform (STL/CLR) | Microsoft Docs"
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
  - "cliext::transform"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉換函式 [STL/CLR]"
ms.assetid: 08940969-6d10-40e4-a35b-68dd801b3949
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# transform (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將指定的函式物件應用至來源中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt, class _Fn1> inline  
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Fn1 _Func);  
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline  
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## 備註  
 這個函式產生與 STL 函式的 `transform`相同的行為。  如需詳細資訊，請參閱[transform](../Topic/transform.md)。  
  
## 需求  
 **標頭：:** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)