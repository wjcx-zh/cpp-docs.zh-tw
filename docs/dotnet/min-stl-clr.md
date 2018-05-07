---
title: min (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::min
dev_langs:
- C++
helpviewer_keywords:
- min function [STL/CLR]
ms.assetid: 7a2c82d1-424c-48a9-a944-adcf95511aef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5449af49537a2a7633048415d06217edbc64783d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="min-stlclr"></a>min (STL/CLR)
比較兩個物件並傳回兩者較小者，其中順序準則可由二元述詞指定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _Ty> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`min`。 如需詳細資訊，請參閱[min](../standard-library/algorithm-functions.md#min)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)