---
title: "high_property_prefixes |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7df4ef6cded98c19ead86160aa772e349ebfd37
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**C + + 特定的**  
  
 為三個屬性方法指定替代的前置詞。  
  
## <a name="syntax"></a>語法  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>參數  
 `GetPrefix`  
 若要使用的前置詞**propget**方法。  
  
 `PutPrefix`  
 若要使用的前置詞**propput**方法。  
  
 `PutRefPrefix`  
 若要使用的前置詞**propputref**方法。  
  
## <a name="remarks"></a>備註  
 根據預設，高階錯誤處理**propget**， **propput**，和**propputref**方法由前置詞的成員函式**取得**， `Put`，和**PutRef**分別。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)