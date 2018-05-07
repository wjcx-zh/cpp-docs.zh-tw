---
title: 取代 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::replace
dev_langs:
- C++
helpviewer_keywords:
- replace function [STL/CLR]
ms.assetid: 3792abca-8d73-476a-8540-c5f739aa48c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7a81bab1fbe77a7fc313e14d8d356abdd480f074
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="replace-stlclr"></a>replace (STL/CLR)
檢查範圍內的每個項目，如果符合指定的值則予以取代。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    void replace(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace`。 如需詳細資訊，請參閱[取代](../standard-library/algorithm-functions.md#replace)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)