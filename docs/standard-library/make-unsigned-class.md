---
title: "make_unsigned 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- make_unsigned
- std::make_unsigned
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
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
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 1bdebf2a3d3f03defa041d049ac98287df7aad6c
ms.lasthandoff: 02/24/2017

---
# <a name="makeunsigned-class"></a>make_unsigned 類別
建立類型，或是建立大於或等於類型大小的最小無正負號類型。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`T`|要修改的類型。|  
  
## <a name="remarks"></a>備註  
 如果 `is_unsigned<T>` 為 true，則 modifier 類型的執行個體所保留的修改類型是 `T`。 否則是最小的帶正負號類型 `ST`，其中 `sizeof (T) <= sizeof (ST)`。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)




