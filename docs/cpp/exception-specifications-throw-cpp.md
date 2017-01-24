---
title: "例外狀況規格 (throw) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, 擲回例外狀況"
  - "例外狀況, 例外狀況規格"
  - "throw 關鍵字 [C++], 例外狀況規格"
  - "throw 關鍵字 [C++], throw() 和 throw(...) 比較"
  - "擲回例外狀況, throw 關鍵字"
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 例外狀況規格 (throw) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

例外狀況規格是在 C\+\+11 中已被取代的 C\+\+ 語言功能。  這些功能是設計用來提供與函式所擲回之例外狀況有關的摘要資訊，但實際上的運作可能會有問題。  其中經過證明有些許用處的例外狀況規格是 throw\(\) 規格。  例如:  
  
```  
void MyFunction(int i) throw();  
```  
  
 通知編譯器，函式不會擲回任何例外狀況。  它相當於使用 [\_\_declspec\(nothrow\)](../cpp/nothrow-cpp.md)。  這是選擇性的功能。  
  
 **\(C\+\+11\)** 在 ISO C\+\+11 Standard 中，引進 [noexcept](../cpp/noexcept-cpp.md) 運算子，並受 Visual Studio 2015 和更新版本所支援。  只要可能，請使用 `noexcept` 指定函式是否可能擲回例外狀況。  
  
 Visual C\+\+ 在其例外狀況規格實作上偏離 ISO C\+\+ 標準。  下表摘要說明 Visual C\+\+ 例外狀況規格實作：  
  
|例外狀況規格|意義|  
|------------|--------|  
|throw\(\)|函式不會擲回例外狀況。  不過，如果例外狀況是從標記為 throw\(\) 的函式擲回，Visual C\+\+ 編譯器不會呼叫 unexpected \(如需詳細資訊，請參閱 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 和 [unexpected](../Topic/unexpected%20\(%3Cexception%3E\).md)\)。  如果函式標記為 throw\(\)，Visual C\+\+ 編譯器假設，此函式不會擲回 C\+\+ 例外狀況並據以產生程式碼。  由於 C\+\+ 編譯器可能執行程式碼最佳化 \(根據函式不會擲回任何 C\+\+ 例外狀況的假設\)，如果函式擲回例外狀況，程式可能無法正確執行。|  
|throw\(...\)|函式會擲回例外狀況。|  
|throw\(`type`\)|函式會擲回類型 `type` 的例外狀況。  不過，在 Visual C\+\+ .NET 中，這會解譯為 throw\(...\)。  請參閱[函式例外狀況指定名稱](../misc/15-4-function-exception-specifiers.md)。|  
  
 如果應用程式中使用例外狀況處理，必須有一個或多個函式可處理擲回的例外狀況。  在擲回例外狀況的函式和處理例外狀況的函式之間呼叫的任何函式，都必須能夠擲回例外狀況。  
  
 函式的 throw 行為取決於下列因素：  
  
-   在 C 或 C\+\+ 中編譯函式。  
  
-   使用哪個 [\/EH](../build/reference/eh-exception-handling-model.md) 編譯器選項。  
  
-   您是否明確指定例外狀況規格。  
  
 C 函式不允許明確例外狀況規格。  
  
 下表摘要說明函式的 throw 行為：  
  
|函式|\/EHsc|\/EHs|\/EHa|\/EHac|  
|--------|------------|-----------|-----------|------------|  
|C 函式|throw\(\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|沒有例外狀況規格的 C\+\+ 函式|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|具有 throw\(\) 例外狀況規格的 C\+\+ 函式|throw\(\)|throw\(\)|throw\(...\)|throw\(...\)|  
|具有 throw\(...\) 例外狀況規格的 C\+\+ 函式|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
|具有 throw\(`type`\) 例外狀況規格的 C\+\+ 函式|throw\(...\)|throw\(...\)|throw\(...\)|throw\(...\)|  
  
## 範例  
  
```cpp  
// exception_specification.cpp  
// compile with: /EHs  
#include <stdio.h>  
  
void handler() {  
   printf_s("in handler\n");  
}  
  
void f1(void) throw(int) {  
   printf_s("About to throw 1\n");  
   if (1)  
      throw 1;  
}  
  
void f5(void) throw() {  
   try {  
      f1();  
   }  
   catch(...) {  
      handler();  
    }  
}  
  
// invalid, doesn't handle the int exception thrown from f1()  
// void f3(void) throw() {  
//   f1();  
// }  
  
void __declspec(nothrow) f2(void) {  
   try {  
      f1();  
   }  
   catch(int) {  
      handler();  
    }  
}  
  
// only valid if compiled without /EHc   
// /EHc means assume extern "C" functions don't throw exceptions  
extern "C" void f4(void);  
void f4(void) {  
   f1();  
}  
  
int main() {  
   f2();  
  
   try {  
      f4();  
   }  
   catch(...) {  
      printf_s("Caught exception from f4\n");  
   }  
   f5();  
}  
```  
  
  **About to throw 1**  
**in handler**  
**About to throw 1**  
**Caught exception from f4**  
**About to throw 1**  
**in handler**   
## 請參閱  
 [try、throw 和 catch 陳述式 \(C\+\+\)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)