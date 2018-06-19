---
title: 填滿 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::fill
dev_langs:
- C++
helpviewer_keywords:
- fill function
ms.assetid: eb67241c-9bb3-497e-bec6-639900c60758
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2e1feaba4690bf64d28a7359b3be17d7e70a96f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107434"
---
# <a name="fill-stlclr"></a>fill (STL/CLR)
將相同的新值指派到指定範圍內的每個項目。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`fill`。 如需詳細資訊，請參閱[填滿](../standard-library/algorithm-functions.md#fill)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)