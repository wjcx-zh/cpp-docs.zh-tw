---
title: "make_unsigned 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::make_unsigned
dev_langs: C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c071aebac468e0feeb8e0964fe04527a29140a5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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



