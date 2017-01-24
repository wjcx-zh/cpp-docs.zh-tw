---
title: "max (STL/CLR) | Microsoft Docs"
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
  - "cliext::max"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max 函式 [STL/CLR]"
ms.assetid: bf51aedc-b7a0-4b6c-a76e-fdbc4af042fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# max (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比較兩個物件並傳回大的一方，其中排序準則可能由二進位述詞指定。  
  
## 語法  
  
```  
template<class _Ty> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
## 備註  
 這個函式產生相同的行為做為 STL 函式的 `max`。  如需詳細資訊，請參閱[max](../Topic/max.md)。  
  
## 需求  
 **標題:** \<cliext\/演算法\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)