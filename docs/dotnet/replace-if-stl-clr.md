---
title: replace_if (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::replace_if
dev_langs:
- C++
helpviewer_keywords:
- replace_if function [STL/CLR]
ms.assetid: 485ed698-551f-4808-8562-9e32b151786d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6685c2dedc32fbe14febb230cc6d34c6aad14aed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33160988"
---
# <a name="replaceif-stlclr"></a>replace_if (STL/CLR)
檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _Pr, class _Ty> inline  
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,  
        const _Ty% _Val);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace_if`。 如需詳細資訊，請參閱[replace_if](../standard-library/algorithm-functions.md#replace_if)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)