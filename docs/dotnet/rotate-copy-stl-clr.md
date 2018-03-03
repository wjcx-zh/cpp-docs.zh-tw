---
title: "rotate_copy (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::rotate_copy
dev_langs:
- C++
helpviewer_keywords:
- rotate_copy function [STL/CLR]
ms.assetid: ed697552-130f-474f-9ab6-133332bb2587
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 19914d41d64c184e66324006c06a0e37e91c6393
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rotatecopy-stlclr"></a>rotate_copy (STL/CLR)
交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _OutIt> inline  
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,  
        _OutIt _Dest);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`rotate_copy`。 如需詳細資訊，請參閱[rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)