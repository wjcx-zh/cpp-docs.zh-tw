---
title: "__clrcall | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__clrcall"
  - "__clrcall_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__clrcall 關鍵字 [C++]"
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# __clrcall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 指定函式只可以從 Managed 程式碼呼叫。針對只會從 Managed 程式碼呼叫的所有虛擬函式使用 `__clrcall`。  不過，這個呼叫慣例不能用於將會從機器碼呼叫的函式。  
  
 從 Managed 函式呼叫虛擬 Managed 函式，或是透過指標從 Managed 函式呼叫 Managed 函式時，使用 `__clrcall` 可改善效能。  
  
 進入點是編譯器產生的不同函式。  如果函式同時具有原生和 Managed 進入點，則其中一個會是具有函式實作的實際函式。  另一個函式將會是呼叫實際函式內部的另一個函式 \(Thunk\)，並且會讓 Common Language Runtime 執行 PInvoke。  將函式標記為 `__clrcall` 時，表示函式實作必須是 MSIL，而且不會產生原生進入點函式。  
  
 在未指定 `__clrcall` 的情況下採用原生函式的位址時，編譯器會使用原生進入點。  `__clrcall` 表示函式為 Managed，而且不需要經歷從 Managed 轉換成原生的過程。  在這種情況下，編譯器會使用 Managed 進入點。  
  
 在使用 **\/clr** \(而不是 **\/clr:pure** 或 **\/clr:safe**\) 且未使用 `__clrcall` 時，採用函式的位址一律會傳回原生進入點函式的位址。  使用 `__clrcall` 時不會建立原生進入點函式，因此您會取得 Managed 函式的位址，而不是進入點 Thunk 函式的位址。  如需詳細資訊，請參閱[Double Thunking](../dotnet/double-thunking-cpp.md)。  
  
 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 表示所有函式和函式指標都是 `__clrcall`，而且編譯器只允許將編譯模組內的函式標記為 `__clrcall`。  使用 **\/clr:pure** 時，`__clrcall` 只能在函式指標和外部宣告上指定。  
  
 只要函式具有 MSIL 實作，您就可以從使用 **\/clr** 編譯的現有 C\+\+ 程式碼直接呼叫 `__clrcall` 函式。  `__clrcall` 函式無法從具有內嵌 asm 且呼叫 CPU 特定內建的函式直接呼叫，即使這些函式是使用 **\/clr** 編譯也一樣。  
  
 `__clrcall` 函式指標僅適用於本身建立所在的應用程式定義域。請不要跨應用程式定義域傳遞 `__clrcall` 函式指標，改為使用 <xref:System.CrossAppDomainDelegate>。  如需詳細資訊，請參閱[應用程式定義域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
## 範例  
  
```  
// clrcall.cpp  
// compile with: /clr:oldSyntax /LD  
void __clrcall Test1( ) {}  
void (__clrcall *fpTest1)( ) = &Test1;  
```  
  
## 範例  
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
  
  **in Func1**  
**&Func1 \!\= pf, comparison fails**  
**in Func1**  
**in Func1**   
## 範例  
 下列範例說明您可以定義函式指標，這樣就表示您宣告函式指標只能從 Managed 程式碼叫用。  如此編譯器就能夠直接呼叫 Managed 函式，並且避開原生進入點 \(雙 Thunk 問題\)。  
  
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
  
## 請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)