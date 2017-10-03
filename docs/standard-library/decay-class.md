---
title: "decay 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 20
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
ms.openlocfilehash: c24872ee58c740776285c715f1d03b16e811d9c6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="decay-class"></a>decay 類別
由值來傳遞時，會產生類型。 可產生非參考、非 const、靜態類型，或從函式或陣列類型建立類型的指標。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
struct decay;

template <class T>  
using decay_t = typename decay<T>::type;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要修改的類型。  
  
## <a name="remarks"></a>備註  
 您可使用 decay 範本產生類型，如同將類型作為引數由值來傳遞一樣。 範本類別成員 typedef `type` 類型所儲存的修改類型，是在下列階段定義：  
  
-   類型 `U` 定義為 `remove_reference<T>::type`。  
  
-   如果 `is_array<U>::value` 為 true，則修改的類型 `type` 為 `remove_extent<U>::type *`。  
  
-   否則，如果 `is_function<U>::value` 為 true，則修改的類型 `type` 為 `add_pointer<U>::type`。  
  
-   否則，修改的類型 `type` 為 `remove_cv<U>::type`。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




