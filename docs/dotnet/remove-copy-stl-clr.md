---
title: "remove_copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::remove_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_copy 函式 [STL/CLR]"
ms.assetid: 602fd8e3-26f7-491f-bf2c-cddf269f9807
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# remove_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製來源範圍的項目到目的範圍，不過，特定值的元素不會複製，不會干擾其他項目的順序和傳回新的目的範圍的結尾。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt remove_copy(_InIt _First, _InIt _Last,  
        _OutIt _Dest, const _Ty% _Val);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `remove_copy` 相同。  如需詳細資訊，請參閱[remove\_copy](../Topic/remove_copy.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)