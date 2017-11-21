---
title: "min_element (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::min_element
dev_langs: C++
helpviewer_keywords: min_element function [STL/CLR]
ms.assetid: 2a9c6828-9722-454f-9c10-d4a184d4d21b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7996e368abff6d82c346ff58eb19d2d53ff208d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="minelement-stlclr"></a>min_element (STL/CLR)
在指定的範圍內尋找第一個最小項目，其中順序準則可由二元述詞指定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`min_element`。 如需詳細資訊，請參閱[min_element](../standard-library/algorithm-functions.md#min_element)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)