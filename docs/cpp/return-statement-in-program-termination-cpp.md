---
title: return 陳述式在程式終止 （c + +） |Microsoft Docs
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
ms.openlocfilehash: eb594eb10e8068d5f5b3ed124d5e77b48ced728e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942628"
---
# <a name="return-statement-in-program-termination-c"></a>程式終止中的 return 陳述式 (C++)
發出`return`陳述式，從**主要**功能上相當於呼叫**結束**函式。 參考下列範例：  
  
```cpp 
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **結束**並**傳回**在上述範例中的陳述式會在功能上完全相同。 不過，c + + 需要具有函式傳回型別以外**void**傳回值。 **會傳回**陳述式可讓您傳回值，以從`main`。  
  
## <a name="see-also"></a>另請參閱  
 [程式終止](../cpp/program-termination.md)