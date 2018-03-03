---
title: "lower_bound (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound function [STL/CLR]
ms.assetid: 841b70b5-1f54-4ecf-8faa-7dda32a24c54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a2e4cbe940ce9eaaa99725a3d252a0275c4fa84e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="lowerbound-stlclr"></a>lower_bound (STL/CLR)
第一個元素的位置中尋找已排序的範圍具有值小於或等於指定的值，其中順序準則可能可由二元述詞指定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`lower_bound`。 如需詳細資訊，請參閱[lower_bound](../standard-library/algorithm-functions.md#lower_bound)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)