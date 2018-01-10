---
title: "raw_property_prefixes |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_property_prefixes
dev_langs: C++
helpviewer_keywords: raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 190a7ce7fbca4fea477771b5c125c96ecc187216
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 根據預設，低階**propget**， **propput**，和**propputref**方法由前置詞的成員函式**get_**， **put_**，和**putref_**分別。 這些前置詞與標頭檔中使用由 MIDL 所產生的名稱相容。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)