---
title: "partial_sum (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::partial_sum
dev_langs: C++
helpviewer_keywords: partial_sum function [STL/CLR]
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8a92858303af5050706849f7e688d08ad36f321
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="partialsum-stlclr"></a>partial_sum (STL/CLR)
計算一系列中的第一個項目，透過輸入範圍內的總和`i`th 項目，並將每個總和的結果`i`個元素的目的範圍，或計算一般化程序的結果，其中總和運算由另一個指定的二進位運算取代。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫的數值函式相同`partial_sum`。 如需詳細資訊，請參閱[partial_sum](../standard-library/numeric-functions.md#partial_sum)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/數字 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)