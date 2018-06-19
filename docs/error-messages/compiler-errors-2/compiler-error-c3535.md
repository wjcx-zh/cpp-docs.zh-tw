---
title: 編譯器錯誤 C3535 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3535
dev_langs:
- C++
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff9935f4a46ba2c3a268ebb761153948ccd82f47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258769"
---
# <a name="compiler-error-c3535"></a>編譯器錯誤 C3535
無法推算 'type1' 從 'type2' 的類型  
  
 所宣告變數的型別`auto`無法初始化運算式的類型推算關鍵字。 例如，這個錯誤發生於初始化運算式評估為`void`，不是型別。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認初始設定運算式的類型不是`void`。  
  
2.  請確認宣告不是基本類型的指標。 如需詳細資訊，請參閱[基本類型](../../cpp/fundamental-types-cpp.md)。  
  
3.  請確定如果宣告類型的指標，初始化運算式是指標類型。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為初始化運算式評估為`void`。  
  
```  
// C3535a.cpp  
// Compile with /Zc:auto  
void f(){}  
int main()  
{  
   auto x = f();   //C3535  
   return 0;  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為陳述式宣告了變數`x`推算的類型，但在初始設定式類型的指標運算式為雙重。 因此，編譯器無法推算變數類型。  
  
```  
// C3535b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto* x = 123.0;   // C3535  
   return 0;  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3535，因為變數`p`宣告指標推算的類型，但初始化運算式不是指標類型。  
  
```  
// C3535c.cpp  
// Compile with /Zc:auto  
class A { };  
A x;  
auto *p = x;  // C3535  
```  
  
## <a name="see-also"></a>另請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)   
 [基本類型](../../cpp/fundamental-types-cpp.md)