---
title: "字元測試 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: ca3c90169a3dab061a1e50e838b3432deec77b0c
ms.lasthandoff: 04/01/2017

---
# <a name="character-testing"></a>字元測試
**ANSI 4.3.1**：以 `isalnum`、`isalpha`、`iscntrl`、`islower`、`isprint` 和 `isupper` 函式測試的字元集  
  
 下表將描述這些函式，因為它們會由 Microsoft C 編譯器實作。  
  
|函式|測試項目|  
|--------------|---------------|  
|`isalnum`|字元 0-9、A-Z、a-z ASCII 48-57、65-90、97-122|  
|`isalpha`|字元 A-Z、a-z ASCII 65-90、97-122|  
|`iscntrl`|ASCII 0 -31、127|  
|`islower`|字元 a-z ASCII 97-122|  
|`isprint`|字元 A-Z、a–z、0-9、標點符號、空格 ASCII 32-126|  
|`isupper`|字元 A-Z ASCII 65-90|  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)
