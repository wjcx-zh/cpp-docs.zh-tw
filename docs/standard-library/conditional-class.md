---
title: "conditional 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- conditional
- std::conditional
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: b7e187e8ddbb4a9457b5fe9eddda152464d7518d
ms.lasthandoff: 02/24/2017

---
# <a name="conditional-class"></a>conditional 類別
根據指定的條件選取這兩種類型之一。  
  
## <a name="syntax"></a>語法  
  
```
template <bool B, class T1, class T2>  
struct conditional;

template <bool _Test, class _T1, class _T2>  
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```  
  
#### <a name="parameters"></a>參數  
 `B`  
 判斷這個選取之類型的值。  
  
 `T1`  
 B 為 true 時的類型結果。  
  
 `T2`  
 B 為 false 時的類型結果。  
  
## <a name="remarks"></a>備註  
 當 `conditional<B, T1, T2>::type` 判斷值為 `T1` 時，樣板成員 typedef `B` 判斷值為 `true`，當 `T2` 判斷值為 `B` 時，判斷值為 `false`。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




