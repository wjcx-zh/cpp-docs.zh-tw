---
title: "stdext 命名空間 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext
dev_langs:
- C++
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 213b760a134a645a0b6552e4c3600fc4762b0bb2
ms.lasthandoff: 02/24/2017

---
# <a name="stdext-namespace"></a>stdext 命名空間
[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 標頭檔的成員目前不是 ISO C++ 標準的一部分。 因此，這些類型和成員已從 `std` 命名空間移至 `stdext`命名空間，以持續符合 C++ 標準。  
  
 使用預設值 [/Ze](../build/reference/za-ze-disable-language-extensions.md) 進行編譯時，編譯器會針對 <hash_map> 和 <hash_set> 標頭檔成員使用 `std` 的情況發出警告。 若要停用警告，請使用 [warning](../preprocessor/warning.md) pragma。  
  
 若要讓編譯器透過 **/Ze**，針對 <hash_map> 和 <hash_set> 標頭檔成員使用 `std` 的情況產生錯誤，請在包含任何 C++ 標準程式庫標頭檔的 #include 前面加入下列指示詞。  
  
```  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  
  
 使用 **/Za**進行編譯時，編譯器會產生錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)


