---
title: "equal (STL/CLR) | Microsoft Docs"
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
  - "cliext::equal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal 函式 [STL/CLR]"
ms.assetid: 7f271666-2198-4e33-8e03-8b73b376c724
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# equal (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比較兩個元素的元素範圍二進位述詞或等值的實際上指定的相等。  
  
## 語法  
  
```  
template<class _InIt1, class _InIt2> inline  
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
        _Pr _Pred);  
```  
  
## 備註  
 這個函式產生與 STL 函式的 `equal`相同的行為。  如需詳細資訊，請參閱[equal](../Topic/equal.md)。  
  
## 需求  
 **標頭：:** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)