---
title: raw_property_prefixes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1f548c9513a086dd4741a9c61c51acebebb25db
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840125"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**C + + 特定的**  
  
 為三個屬性方法指定替代的前置詞。  
  
## <a name="syntax"></a>語法  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>參數  
 `GetPrefix`  
 若要使用的前置詞**propget**方法。  
  
 `PutPrefix`  
 若要使用的前置詞**propput**方法。  
  
 `PutRefPrefix`  
 若要使用的前置詞**propputref**方法。  
  
## <a name="remarks"></a>備註  
 根據預設，低階**propget**， **propput**，和**propputref**方法由前置詞的成員函式**get_**， **put_**，和**putref_** 分別。 這些前置詞與標頭檔中使用由 MIDL 所產生的名稱相容。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)