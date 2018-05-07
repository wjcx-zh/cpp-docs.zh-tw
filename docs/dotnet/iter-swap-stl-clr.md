---
title: iter_swap (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::iter_swap
dev_langs:
- C++
helpviewer_keywords:
- iter_swap function [STL/CLR]
ms.assetid: 9809c9f5-2ca6-4e9e-97c1-d7973d3134f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99e24ccbecea583de2a86b3c88a0180b016eae92
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iterswap-stlclr"></a>iter_swap (STL/CLR)
交換由一組指定之迭代器所參考的兩個值。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt1, class _FwdIt2> inline  
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`iter_swap`。 如需詳細資訊，請參閱[iter_swap](../standard-library/algorithm-functions.md#iter_swap)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)