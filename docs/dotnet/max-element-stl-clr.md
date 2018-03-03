---
title: "max_element (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::max_element
dev_langs:
- C++
helpviewer_keywords:
- max_element function [STL/CLR]
ms.assetid: c6274bae-1216-4285-b395-254280253dae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aebe6addd047130918ce16718122ff42cebb0cd0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="maxelement-stlclr"></a>max_element (STL/CLR)
在指定的範圍內尋找第一個最大項目，其中順序準則可由二元述詞指定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`max_element`。 如需詳細資訊，請參閱[max_element](../standard-library/algorithm-functions.md#max_element)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)