---
title: generate_n (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::generate_n
dev_langs:
- C++
helpviewer_keywords:
- generate_n function [STL/CLR]
ms.assetid: 2f56e649-7a6f-4861-ae49-d0b25f5cd50c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0072d3694c058d0951e55b09ee6a2a376cbe94a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="generaten-stlclr"></a>generate_n (STL/CLR)
將函式物件產生的值指派給範圍內的指定項目數，並返回到超過最後一個指定值的位置。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _OutIt, class _Diff, class _Fn0> inline  
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`generate_n`。 如需詳細資訊，請參閱[generate_n](../standard-library/algorithm-functions.md#generate_n)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)