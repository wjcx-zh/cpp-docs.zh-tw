---
title: "replace (STL/CLR) | Microsoft Docs"
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
  - "cliext::replace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "replace 函式 [STL/CLR]"
ms.assetid: 3792abca-8d73-476a-8540-c5f739aa48c2
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# replace (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檢查在範圍內的每一個項目，若符合指定值則取代它。  
  
## 語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `replace` 相同。  如需詳細資訊，請參閱[取代](../Topic/replace.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)