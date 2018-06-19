---
title: binary_search (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::binary_search
dev_langs:
- C++
helpviewer_keywords:
- binary_search function [STL/CLR]
ms.assetid: 520869cc-7cd3-4c81-b439-05f042474416
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 467efdb6c17dd6f3d9dcf8b7aa8b3495367a92f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105292"
---
# <a name="binarysearch-stlclr"></a>binary_search (STL/CLR)
測試已排序的範圍中是否有等於指定之值 (或在二元述詞指定的意義上，相當於該值) 的項目。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _FwdIt, class _Ty> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`binary_search`。 如需詳細資訊，請參閱[binary_search](../standard-library/algorithm-functions.md#binary_search)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)