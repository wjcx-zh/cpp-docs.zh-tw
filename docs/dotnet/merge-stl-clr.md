---
title: merge (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::merge
dev_langs:
- C++
helpviewer_keywords:
- merge function [STL/CLR]
ms.assetid: e42d3396-63a4-438a-964d-83e90405102e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 09f9cc8d81eb4862607d2382f7d3d2ac033cf111
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="merge-stlclr"></a>merge (STL/CLR)
將兩個排序來源範圍內的所有項目結合成單一排序目的範圍，其中順序準則可由二元述詞指定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`merge`。 如需詳細資訊，請參閱[合併](../standard-library/algorithm-functions.md#merge)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)