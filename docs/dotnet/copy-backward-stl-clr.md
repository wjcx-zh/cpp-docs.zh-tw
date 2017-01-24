---
title: "copy_backward (STL/CLR) | Microsoft Docs"
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
  - "cliext::copy_backward"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copy_backward 函式 [STL/CLR]"
ms.assetid: 649db3fd-5a79-44b6-bea9-ecbcbeba1f32
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# copy_backward (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定從來源範圍的到目的範圍項目的值，逐一查看項目來源序列並指派它們以反向的新位置。  
  
## 語法  
  
```  
template<class _BidIt1, class _BidIt2> inline  
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,  
        _BidIt2 _Dest);  
```  
  
## 備註  
 這個函式的行為與 STL 函式 `copy_backward` 相同。  如需詳細資訊，請參閱[copy\_backward](../Topic/copy_backward.md)。  
  
## 需求  
 **標頭：** \<cliext\/algorithm\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [algorithm](../dotnet/algorithm-stl-clr.md)