---
title: "stdext 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_DEFINE_DEPRECATED_HASH_CLASSES 符號"
  - "stdext 命名空間"
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# stdext 命名空間
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 標頭檔的成員目前不是 ISO C\+\+ 標準的一部分。 因此，這些類型和成員已從 `std` 命名空間移至 `stdext` 命名空間，以持續符合 C\+\+ 標準。  
  
 使用預設值 [\/Ze](../build/reference/za-ze-disable-language-extensions.md) 進行編譯時，編譯器會針對 \<hash\_map\> 和 \<hash\_set\> 標頭檔成員使用 `std` 的情況發出警告。 若要停用警告，請使用 [warning](../preprocessor/warning.md) pragma。  
  
 若要讓編譯器透過 **\/Ze**，針對 \<hash\_map\> 和 \<hash\_set\> 標頭檔成員使用 `std` 的情況產生錯誤，請在包含任何 Standard C\+\+ 程式庫標頭檔的 \#include 前面加入下列指示詞。  
  
```  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  
  
 使用 **\/Za** 進行編譯時，編譯器會產生錯誤。  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)