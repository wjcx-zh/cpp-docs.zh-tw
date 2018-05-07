---
title: replace_copy (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::replace_copy
dev_langs:
- C++
helpviewer_keywords:
- replace_copy function [STL/CLR]
ms.assetid: b531b49b-b16d-4b04-8f80-74f43dd496a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a027bbf1374988d79b94585f0d303c7e352ddbee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="replacecopy-stlclr"></a>replace_copy (STL/CLR)
檢查來源範圍內的每個項目，如果符合指定的值則予以取代，同時將結果複製到新目的範圍。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`replace_copy`。 如需詳細資訊，請參閱[replace_copy](../standard-library/algorithm-functions.md#replace_copy)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)