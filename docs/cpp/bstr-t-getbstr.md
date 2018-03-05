---
title: "_bstr_t::GetBSTR |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b2f7f487673c67aa7b681499462ea05a471b48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Microsoft 特定的**  
  
 指向由 `BSTR` 所包裝之 `_bstr_t` 的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 由 `BSTR` 所包裝之 `_bstr_t` 的開頭。  
  
## <a name="remarks"></a>備註  
 `GetBSTR` 會影響所有共用 `_bstr_t` 的 `BSTR` 物件。 一個以上的 `_bstr_t` 可以使用複製建構函式和 `BSTR` 來共用 `operator=`。  
  
## <a name="example"></a>範例  
 請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用範例`GetBSTR`。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_bstr_t 類別](../cpp/bstr-t-class.md)