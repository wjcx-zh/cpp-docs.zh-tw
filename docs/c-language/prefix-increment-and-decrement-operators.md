---
title: 前置遞增和遞減運算子 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, types of
- decrement operators, syntax
- decrement operators
ms.assetid: 9a441bb9-d94a-4b6a-9db2-0d0d76bc480d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116921ea46418db5c8eff3327de73a40aa42533c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="prefix-increment-and-decrement-operators"></a>前置遞增和遞減運算子
當遞增或遞減運算子出現在運算元前面時，一元運算子 (`++` 和 **--**) 稱為「前置」遞增或遞減運算子。 後置遞增和遞減的優先順序高於前置遞增和遞減。 運算元必須有整數類資料、浮點或指標類型，並且必須是可修改的左值運算式 (沒有 **const** 屬性的運算式)。 結果為左值。  
  
 當運算子出現在其運算元前面時，運算元會遞增或遞減，而其新值是運算式的結果。  
  
 整數或浮點類型的運算元會以整數值 1 遞增或遞減。 結果的類型與運算元類型相同。 指標類型的運算元會以其定址之物件的大小遞增或遞減。 遞增指標會指向下一個物件，遞減指標則指向上一個物件。  
  
## <a name="example"></a>範例  
 這個範例將說明一元前置遞減運算子：  
  
```  
if( line[--i] != '\n' )  
    return;  
```  
  
 在這個範例中，`i` 變數會先遞減，再做為 `line` 的註標使用。  
  
## <a name="see-also"></a>請參閱  
 [C 一元運算子](../c-language/c-unary-operators.md)