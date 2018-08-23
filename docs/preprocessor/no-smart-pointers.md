---
title: no_smart_pointers |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 345da5de492c33107effffb9c97b2fe60906e899
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538602"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**C + + 特定**  
  
不為類型程式庫中的所有介面建立智慧型指標。  
  
## <a name="syntax"></a>語法  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>備註  
 
根據預設，當您使用 `#import` 時，會得到類型程式庫中所有介面的智慧型指標宣告。 這些智慧型指標的類型是[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)