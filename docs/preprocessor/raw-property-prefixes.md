---
title: raw_property_prefixes |Microsoft Docs
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
ms.openlocfilehash: 423a66b698f4e421ff29e6ac3dfddd11fa11c58f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42543096"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**C + + 特定**  
  
為三個屬性方法指定替代的前置詞。  
  
## <a name="syntax"></a>語法  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>參數  
*GetPrefix*  
若要使用的前置詞`propget`方法。  
  
*PutPrefix*  
若要使用的前置詞`propput`方法。  
  
*PutRefPrefix*  
若要使用的前置詞`propputref`方法。  
  
## <a name="remarks"></a>備註  
 
根據預設，低階`propget`， `propput`，並`propputref`方法會公開由成員函式的名稱前置詞**get_**， **put_**，和**putref_** 分別。 這些前置詞與標頭檔中使用由 MIDL 所產生的名稱相容。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)