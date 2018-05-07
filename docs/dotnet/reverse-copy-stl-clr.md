---
title: reverse_copy (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::reverse_copy
dev_langs:
- C++
helpviewer_keywords:
- reverse_copy function [STL/CLR]
ms.assetid: 694e577a-0fa8-44f7-adde-6dd9f45adefd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cdc17fc5dc5b8007bbe1f478e250f31792e76a40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="reversecopy-stlclr"></a>reverse_copy (STL/CLR)
反轉來源範圍內項目的順序，將其複製到目的範圍。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`reverse_copy`。 如需詳細資訊，請參閱[reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)