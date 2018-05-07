---
title: copy_backward (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::copy_backward
dev_langs:
- C++
helpviewer_keywords:
- copy_backward function [STL/CLR]
ms.assetid: 649db3fd-5a79-44b6-bea9-ecbcbeba1f32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5ff5b52b356d4601ac671f148a4b0464f69f3a16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="copybackward-stlclr"></a>copy_backward (STL/CLR)
從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以反向方向指派它們新位置。  
  
## <a name="syntax"></a>語法  
  
```  
template<class _BidIt1, class _BidIt2> inline  
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,  
        _BidIt2 _Dest);  
```  
  
## <a name="remarks"></a>備註  
 此函式的行為與 c + + 標準程式庫函式相同`copy_backward`。 如需詳細資訊，請參閱[copy_backward](../standard-library/algorithm-functions.md#copy_backward)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<演算法 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)