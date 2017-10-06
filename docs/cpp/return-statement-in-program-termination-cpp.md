---
title: "return 陳述式在程式終止 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: f5ba078ef364a046a9e635d8b2632558e426f4b8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

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
