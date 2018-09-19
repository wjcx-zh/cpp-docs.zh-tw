---
title: make_exception_ptr 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ppltasks/std::make_exception_ptr
dev_langs:
- C++
ms.assetid: 8d81cf7a-818e-4b27-8d49-440ec3088609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3f483d266b8150dfd4aaa5299ffec280d447157
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037615"
---
# <a name="makeexceptionptr-function"></a>make_exception_ptr 函式
## <a name="syntax"></a>語法  
  
```
template<class _E>
exception_ptr make_exception_ptr(_E _Except);
```  
  
#### <a name="parameters"></a>參數  
*_E*<br/>
例外狀況類型。

*_Except*<br/>
例外狀況值。
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** ppltasks.h  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [std 命名空間](std-namespace.md)
