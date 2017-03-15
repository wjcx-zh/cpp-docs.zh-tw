---
title: "編譯器錯誤 C3063 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3063
dev_langs:
- C++
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
caps.latest.revision: 9
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: ce6a597e0246cee5c62dd6612d48fe4946505e77
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3063"></a>編譯器錯誤 C3063
運算子 'operator': 所有運算元都必須都具有相同的列舉型別  
  
時使用列舉值的運算子，這兩個運算元必須是列舉型別。 如需詳細資訊，請參閱[How to︰ 定義和使用列舉，在 C + + /cli CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3063，並示範如何修正此問題︰  
  
```  
// C3063.cpp  
// compile with: /clr  
enum class E { a, b } e, mask;  
int main() {  
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```
