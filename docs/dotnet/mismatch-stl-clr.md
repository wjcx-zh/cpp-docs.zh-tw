---
title: "不相符 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::mismatch
dev_langs:
- C++
helpviewer_keywords:
- mismatch function [STL/CLR]
ms.assetid: 77876875-44bb-4476-afd9-390da4eaac16
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8e08b5280b378c55ef0b3144522f6af6cafbc7c1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mismatch-stlclr"></a>mismatch (STL/CLR)
逐一比較兩個範圍的每個項目是否相等 (或在二元述詞指定的意義上，是否對等)，而且找出差異發生的第一個位置。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt1, class _InIt2> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
            _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`mismatch`。 如需詳細資訊，請參閱[不符](../standard-library/algorithm-functions.md#mismatch)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)