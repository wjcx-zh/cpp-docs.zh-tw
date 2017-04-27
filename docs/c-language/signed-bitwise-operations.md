---
title: "帶正負號的位元運算 | Microsoft Docs"
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
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
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
ms.openlocfilehash: e3e4eeb1c71752c7e682bc500afacb730162abca
ms.lasthandoff: 04/01/2017

---
# <a name="signed-bitwise-operations"></a>帶正負號的位元運算
**ANSI 3.3**：帶正負號整數位元運算的結果  
  
 帶正負號整數的位元運算運作方式，與不帶正負號整數的位元運算相同。 例如，`-16 & 99` 可以用二進位運算式表示為  
  
```  
  11111111 11110000  
& 00000000 01100011  
  _________________  
  00000000 01100000  
```  
  
 位元 AND 的結果為 96。  
  
## <a name="see-also"></a>另請參閱  
 [整數](../c-language/integers.md)
