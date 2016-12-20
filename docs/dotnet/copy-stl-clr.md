---
title: "copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copy 函式 [STL/CLR]"
ms.assetid: f6738535-fde6-446e-a797-bf2b457c2bff
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定從來源範圍的到目的範圍，逐一查看項目來源序列並將這些值的方向是往前項目值的新位置。  
  
## 語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `copy`。  如需詳細資訊，請參閱[copy](../Topic/copy.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)