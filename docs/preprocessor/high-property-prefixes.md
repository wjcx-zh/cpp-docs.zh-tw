---
title: high_property_prefixes |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ce21958dbb928a29debe21fb7cfaed4b9036141
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540163"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**C + + 特定**  
  
為三個屬性方法指定替代的前置詞。  
  
## <a name="syntax"></a>語法  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>參數  
*GetPrefix*  
若要使用的前置詞`propget`方法。  
  
*PutPrefix*  
若要使用的前置詞`propput`方法。  
  
*PutRefPrefix*  
若要使用的前置詞`propputref`方法。  
  
## <a name="remarks"></a>備註  
 
根據預設，高階錯誤處理`propget`， `propput`，並`propputref`方法會公開由成員函式名稱前置詞`Get`， `Put`，和`PutRef`分別。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)