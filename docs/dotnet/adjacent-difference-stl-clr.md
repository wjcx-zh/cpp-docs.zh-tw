---
title: "adjacent_difference (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::adjacent_difference
dev_langs: C++
helpviewer_keywords: adjacent_difference function
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0be63f7032de5f6d3def4ba74f24a346785b7391
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="adjacentdifference-stlclr"></a>adjacent_difference (STL/CLR)
計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫的數值函式相同`adjacent_difference`。 如需詳細資訊，請參閱[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/數字 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)