---
title: "編譯器錯誤 C3485 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3485
dev_langs: C++
helpviewer_keywords: C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd49b93beb54776bf17a9ee2bc5c9816f0964451
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3485"></a>編譯器錯誤 C3485
Lambda 定義不能有任何 cv 限定詞  
  
 您不能使用 `const` 或 `volatile` 限定詞作為 Lambda 運算式定義的一部分。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請從 Lambda 運算式的定義中移除 `const` 或 `volatile` 限定詞。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3485，因為它使用 `const` 限定詞作為 Lambda 運算式定義的一部分：  
  
```  
// C3485.cpp  
  
int main()  
{  
   auto x = []() const mutable {}; // C3485  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)