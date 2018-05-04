---
title: return 陳述式在程式終止 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61d09c1b3aaea799c227686436486efa48fc7857
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-in-program-termination-c"></a>程式終止中的 return 陳述式 (C++)
發出`return`陳述式從**主要**功能上相當於呼叫**結束**函式。 參考下列範例：  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **結束**和`return`在上述範例中的陳述式會運作方式相同。 不過，C++ 要求使用具有傳回類型 (非 `void`) 的函式傳回一個值。 `return`陳述式可讓您傳回值，以從**主要**。  
  
## <a name="see-also"></a>另請參閱  
 [程式終止](../cpp/program-termination.md)