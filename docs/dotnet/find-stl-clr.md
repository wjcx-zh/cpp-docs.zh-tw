---
title: 尋找 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::find
dev_langs:
- C++
helpviewer_keywords:
- find function [STL/CLR]
ms.assetid: 88391e24-1239-4087-b1c2-96efba0337c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 36447eaf3fb62bf5dedbe91213a98308599854f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="find-stlclr"></a>find (STL/CLR)
在範圍中找出有指定值的第一個項目的位置。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt, class _Ty> inline  
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`find`。 如需詳細資訊，請參閱[尋找](../standard-library/algorithm-functions.md#find)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)