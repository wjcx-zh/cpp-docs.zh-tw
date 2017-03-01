---
title: "identity 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::identity
- utility/std::identity
- identity
- std.identity
dev_langs:
- C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a7404d2c1a785fd66489421fd7b9689260e0986d
ms.lasthandoff: 02/24/2017

---
# <a name="identity-structure"></a>identity 結構
一種提供類型定義來作為範本參數的結構。  
  
## <a name="syntax"></a>語法  
```  
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };  
```  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`left`|要識別的值。|  
  
## <a name="remarks"></a>備註  
 此類別包含公用類型定義 `type`，這與範本參數 Type 相同。 它是與範本函式 [forward](../standard-library/utility-functions.md#forward) 搭配使用，以確保函式參數具有所需的類型。  
  
 為了與舊版程式碼相容，此類別也會定義識別函式 `operator()`，此函式會傳回其引數 `left`。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<utility>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [\<utility>](../standard-library/utility.md)




