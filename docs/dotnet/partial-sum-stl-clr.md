---
title: partial_sum (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::partial_sum
dev_langs:
- C++
helpviewer_keywords:
- partial_sum function [STL/CLR]
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c8141e93d7c8101c9bbfaea08c317748cd44f87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33159154"
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