---
title: "is_nothrow_copy_constructible 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79a1745aeee861d898518540a43438f2304cbb35
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible 類別
測試類型是否具有 **nothrow** 複製建構函式。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct is_nothrow_copy_constructible;
```  
  
#### <a name="parameters"></a>參數  
 `Ty`  
 要查詢的類型。  
  
## <a name="remarks"></a>備註  
 如果類型 `Ty` 具有 nothrow 複製建構函式，則述詞類型的執行個體為 true，否則為 false。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [<type_traits>](../standard-library/type-traits.md)





