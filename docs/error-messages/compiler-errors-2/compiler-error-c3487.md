---
title: "編譯器錯誤 C3487 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3487
dev_langs: C++
helpviewer_keywords: C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb659f2d7971d1dd2ff27c438839336d4744767e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3487"></a>編譯器錯誤 C3487
'return type'：所有傳回運算式必須推算為相同類型：先前是 'return type'  
  
 Lambda 必須指定其傳回型別，除非它包含單一 return 陳述式。 如果 Lambda 包含多個 return 陳述式，則必須有相同的類型。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   指定 Lambda 的尾端傳回類型。 確認所有從 Lambda 的傳回型別皆相同，或是隱含地轉換為傳回型別。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3487，因為 Lambda 的傳回型別不相符：  
  
```  
// C3487.cpp  
// Compile by using: cl /c /W4 C3487.cpp  
  
int* test(int* pi) {  
   // To fix the error, uncomment the trailing return type below  
   auto odd_pointer = [=]() /* -> int* */ {  
      if (*pi % 2)   
         return pi;  
      return nullptr; // C3487 - nullptr is not an int* type  
   };  
   return odd_pointer();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)