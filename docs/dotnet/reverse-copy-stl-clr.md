---
title: "reverse_copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::reverse_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_copy 函式 [STL/CLR]"
ms.assetid: 694e577a-0fa8-44f7-adde-6dd9f45adefd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# reverse_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在將其複製到目的範圍時，在來源範圍內反轉項目的順序。  
  
## 語法  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `reverse_copy` 相同。  如需詳細資訊，請參閱[reverse\_copy](../Topic/reverse_copy.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)