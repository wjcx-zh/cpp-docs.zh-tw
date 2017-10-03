---
title: "make_signed 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::make_signed
dev_langs:
- C++
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
caps.latest.revision: 18
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 710f73961b7c31b106d796bfe8935ac6b297072a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="makesigned-class"></a>make_signed 類別
建立類型，或是建立大於或等於類型大小的最小帶正負號類型。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要修改的類型。  
  
## <a name="remarks"></a>備註  
 如果 `is_signed<T>` 為 true，則 modifier 類型的執行個體所保留的修改類型是 `T`。 否則，是最小的未帶正負號類型 `UT`，其中 `sizeof (T) <= sizeof (UT)`。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




