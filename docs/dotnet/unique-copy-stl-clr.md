---
title: unique_copy (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::unique_copy
dev_langs:
- C++
helpviewer_keywords:
- unique_copy function [STL/CLR]
ms.assetid: 37aa5b06-42c5-420d-94c5-00f00ad26471
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ab28fbf26151d1ffc1d1c6524b73f325fce94ff2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164067"
---
# <a name="uniquecopy-stlclr"></a>unique_copy (STL/CLR)
將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`unique_copy`。 如需詳細資訊，請參閱[unique_copy](../standard-library/algorithm-functions.md#unique_copy)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)