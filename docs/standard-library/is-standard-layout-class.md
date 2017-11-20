---
title: "is_standard_layout 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 41d0472a031904fbb40d381aa6113da17feb3e1b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="isstandardlayout-class"></a>is_standard_layout 類別
測試類型是否為標準配置。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct is_standard_layout;
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|`Ty`|要查詢的類型|  
  
## <a name="remarks"></a>備註  
 如果類型 `Ty` 在記憶體中是具有成員物件之標準配置的類別，則類型述詞的執行個體會保留 true，否則保留 false。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<type_traits>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [<type_traits>](../standard-library/type-traits.md)



