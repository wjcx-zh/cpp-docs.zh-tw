---
title: "equal_range (STL/CLR) | Microsoft Docs"
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
  - "cliext::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_range 函式 [STL/CLR]"
ms.assetid: 1b2e76c3-6b52-486d-9785-2639b54277fd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尋找一組已排序的範圍、第一個小於或等於的位置設定為指定的項目和第二個大於的位置項目的位置，其中會使用等價或定序感覺建立序列中的位置可能由二進位述詞指定。  
  
## 語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `equal_range` 相同。  如需詳細資訊，請參閱[equal\_range](../Topic/equal_range.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)