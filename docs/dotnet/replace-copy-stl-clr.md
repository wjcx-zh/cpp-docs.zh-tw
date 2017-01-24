---
title: "replace_copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::replace_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "replace_copy 函式 [STL/CLR]"
ms.assetid: b531b49b-b16d-4b04-8f80-74f43dd496a4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# replace_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檢查來源範圍的每個項目並取代它，則符合指定值，當複製結果載入至新的範圍。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `replace_copy`。  如需詳細資訊，請參閱[replace\_copy](../Topic/replace_copy.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)