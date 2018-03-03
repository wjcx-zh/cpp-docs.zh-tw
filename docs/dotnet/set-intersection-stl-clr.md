---
title: "set_intersection (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::set_intersection
dev_langs:
- C++
helpviewer_keywords:
- set_intersection function [STL/CLR]
ms.assetid: 8a799b20-55a5-4fba-a9c1-a48597cbdae6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3647893f3025621aa5c95eb4023b76e06ac596b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setintersection-stlclr"></a>set_intersection (STL/CLR)
將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt1, class _InIt2, class _OutIt> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);  
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline  
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,  
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`set_intersection`。 如需詳細資訊，請參閱[set_intersection](../standard-library/algorithm-functions.md#set_intersection)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)