---
title: 累積 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::accumulate
dev_langs:
- C++
helpviewer_keywords:
- accumulate function [STL/CLR]
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 128fe8e46c24b8e0595fe19c0075933d3e5069a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="accumulate-stlclr"></a>accumulate (STL/CLR)
藉由計算連續的部分總和來計算指定範圍內所有元素 (包括某個初始值) 的總和，或是計算連續部分結果 (同樣是使用指定的二進位運算而非加總來計算出) 的結果。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫的數值函式相同`accumulate`。 如需詳細資訊，請參閱[累積](../standard-library/numeric-functions.md#accumulate)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/數字 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)