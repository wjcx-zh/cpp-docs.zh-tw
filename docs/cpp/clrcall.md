---
title: "__clrcall |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __clrcall_cpp
dev_langs: C++
helpviewer_keywords: __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d216e196f4b23deb7916bd4d9255c32d782ababb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="clrcall"></a>__clrcall
**Microsoft 特定的**  
  
 指定函式只可以從 Managed 程式碼呼叫。  針對只會從 Managed 程式碼呼叫的所有虛擬函式使用 `__clrcall`。 不過，這個呼叫慣例不能用於將會從機器碼呼叫的函式。  
  
 從 Managed 函式呼叫虛擬 Managed 函式，或是透過指標從 Managed 函式呼叫 Managed 函式時，使用 `__clrcall` 可改善效能。  
  
 進入點是編譯器產生的不同函式。 如果函式同時具有原生和 Managed 進入點，則其中一個會是具有函式實作的實際函式。 另一個函式將會是呼叫實際函式內部的另一個函式 (Thunk)，並且會讓 Common Language Runtime 執行 PInvoke。 將函式標記為 `__clrcall` 時，表示函式實作必須是 MSIL，而且不會產生原生進入點函式。  
  
 在未指定 `__clrcall` 的情況下採用原生函式的位址時，編譯器會使用原生進入點。 `__clrcall` 表示函式為 Managed，而且不需要經歷從 Managed 轉換成原生的過程。 在這種情況下，編譯器會使用 Managed 進入點。  
  
 時**/clr** (不**/clr: pure**或**/clr: safe**) 會使用和`__clrcall`是未使用，會一律採用函式的位址傳回的原生進入位址點函式。 使用 `__clrcall` 時不會建立原生進入點函式，因此您會取得 Managed 函式的位址，而不是進入點 Thunk 函式的位址。 如需詳細資訊，請參閱[Double Thunking](../dotnet/double-thunking-cpp.md)。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 [/clr （common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)意味著所有函式和函式指標都是`__clrcall`，編譯器不會允許內部標示任何項目以外的編譯的函數`__clrcall`。 當**/clr: pure**使用時，`__clrcall`只能在函式指標和外部宣告上指定。  
  
 您可以直接呼叫`__clrcall`函式編譯使用現有 c + + 程式碼從**/clr** ，只要該函式具有 MSIL 實作。 `__clrcall`無法直接從具有內嵌 asm 且呼叫 CPU 特定內，例如，函式呼叫函式，即使這些函式會以編譯**/clr**。  
  
 `__clrcall` 函式指標僅適用於本身建立所在的應用程式定義域。  請不要跨應用程式定義域傳遞 `__clrcall` 函式指標，改為使用 <xref:System.CrossAppDomainDelegate>。 如需詳細資訊，請參閱[應用程式定義域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)。  
  
## <a name="example"></a>範例  
 請注意，使用 `__clrcall` 宣告函式時，會在需要時產生程式碼，例如在呼叫函式時。  
  
```  
// clrcall2.cpp  
// compile with: /clr  
using namespace System;  
int __clrcall Func1() {  
   Console::WriteLine("in Func1");  
   return 0;  
}  
  
// Func1 hasn't been used at this point (code has not been generated),   
// so runtime returns the adddress of a stub to the function  
int (__clrcall *pf)() = &Func1;  
  
// code calls the function, code generated at difference address  
int i = pf();   // comment this line and comparison will pass  
  
int main() {  
   if (&Func1 == pf)  
      Console::WriteLine("&Func1 == pf, comparison succeeds");  
   else   
      Console::WriteLine("&Func1 != pf, comparison fails");  
  
   // even though comparison fails, stub and function call are correct  
   pf();  
   Func1();  
}  
```  
  
```Output  
in Func1  
&Func1 != pf, comparison fails  
in Func1  
in Func1  
```  
  
## <a name="example"></a>範例  
 下列範例說明您可以定義函式指標，這樣就表示您宣告函式指標只能從 Managed 程式碼叫用。 如此編譯器就能夠直接呼叫 Managed 函式，並且避開原生進入點 (雙 Thunk 問題)。  
  
```  
// clrcall3.cpp  
// compile with: /clr  
void Test() {  
   System::Console::WriteLine("in Test");  
}  
  
int main() {  
   void (*pTest)() = &Test;  
   (*pTest)();  
  
   void (__clrcall *pTest2)() = &Test;  
   (*pTest2)();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [關鍵字](../cpp/keywords-cpp.md)