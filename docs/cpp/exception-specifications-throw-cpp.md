---
title: "例外狀況規格 (throw) （c + +） |Microsoft 文件"
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
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++], throw() vs. throw(...)
- throw keyword [C++], exception specifications
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: 20
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
ms.openlocfilehash: 6577cf489ee1c9d64689938bb8a12660cec96893
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="exception-specifications-throw-noexcept-c"></a>例外狀況規格 （throw、 noexcept） （c + +）
例外狀況規格是 c + + 語言功能，以指出例外狀況類型的函式進行傳播相關的程式設計人員的目的。 您可以指定函式可能會或可能不會結束例外狀況使用*例外狀況規格*。 編譯器可以使用這項資訊來最佳化呼叫函式，並以結束程式。 如果預期的例外狀況逸出函式。 有兩種類型的例外狀況規格。 *Noexcept 規格*C + + 11 的新功能。 它會指定可能的例外狀況可以逸出函式的集合是否為空白。 *動態例外狀況規格*，或`throw(optional_type_list)`規格，在 C + + 11 中已被取代，僅部分支援 Visual Studio。 此例外狀況規格設計來提供離函式，可以擲回例外狀況的摘要資訊，但實際上它找不到問題。 經過證明有些許用處一個動態例外狀況規格是無條件`throw()`規格。 例如，函式宣告：  
  
```cpp  
void MyFunction(int i) throw();  
```  
  
 通知編譯器，函式不會擲回任何例外狀況。 它相當於使用[__declspec （nothrow)](../cpp/nothrow-cpp.md)。 這是選擇性的功能。  
  
ISO C + + 11 標準中， [noexcept](../cpp/noexcept-cpp.md)運算子導入成取代。 支援在 Visual Studio 2015 和更新版本。 您應該盡可能使用`noexcept`運算式來指定函式可能會擲回例外狀況。 比方說，使用這個函式宣告，而不是上述其中一個：  
  
```cpp  
void MyFunction(int i) noexcept;  
```  
  
雖然 Visual c + + 完全支援`noexcept`運算式，它偏離 ISO c + + 標準在動態例外狀況規格實作。  下表摘要說明 Visual C++ 例外狀況規格實作：  
  
|例外狀況規格|意義|  
|-----------------------------|-------------|  
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|函式不會擲回例外狀況。 不過，如果例外狀況會擲回離函式標示為`throw()`，Visual c + + 編譯器會呼叫`std::terminate`，而非`std::unexpected`。 請參閱[std::unexpected](../c-runtime-library/reference/unexpected-crt.md)如需詳細資訊。 如果函式標示為`noexcept`， `noexcept(true)`，或`throw()`，Visual c + + 編譯器會假設函式不會擲回 c + + 例外狀況，並據此產生程式碼。 因為 c + + 編譯器假設，此函式不會擲回任何 c + + 例外狀況，如果函式並擲回例外狀況，可能會執行程式碼最佳化，程式可能無法正確執行。|  
|`noexcept(false)`<br/>`throw(...)`<br/>無規格|此函式會擲回任何類型的例外狀況。|  
|`throw(type)`|函式會擲回類型 `type` 的例外狀況。 在 Visual c + + 中，此語法會被接受，但將它解譯為`noexcept(false)`。|  
  
 如果應用程式中使用例外狀況處理，必須有函式擲回例外狀況之前離開函式的外部範圍的控點標示之呼叫堆疊中`noexcept`， `noexcept(true)`，或`throw()`。 如果任何函式呼叫之間會將所擲回例外狀況和處理例外狀況的一個指定為`noexcept`， `noexcept(true)`，或`throw()`，當 noexcept 函式傳播例外狀況時，會終止程式。  
  
 函式的例外狀況行為取決於下列因素：  
  
-   在 C 或 C++ 中編譯函式。  
  
-   其中[/EH](../build/reference/eh-exception-handling-model.md)您使用的編譯器選項。  
  
-   您是否明確指定例外狀況規格。  
  
 C 函式不允許明確例外狀況規格。 C 函式會假設不擲回例外狀況下的**/EHsc**，可能會擲回下的結構化例外狀況和**/EHs**， **/EHa**，或**/EHac**。  
  
 下表摘要說明是否可能會在各種編譯器例外狀況處理選項可能會擲回 c + + 函式：  
  
|函式|/EHsc|/EHs|/EHa|/EHac|  
|--------------|------------|-----------|-----------|------------|  
|沒有例外狀況規格的 C++ 函式|是|是|是|是|  
|具有 c + + 函式`noexcept`， `noexcept(true)`，或`throw()`例外狀況規格|否|否|是|是|  
|具有 c + + 函式`noexcept(false)`， `throw(...)`，或`throw(type)`例外狀況規格|是|是|是|是|  
  
## <a name="example"></a>範例  
  
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
  
```Output  
About to throw 1  
in handler  
About to throw 1  
Caught exception from f4  
About to throw 1  
in handler  
```  
  
## <a name="see-also"></a>另請參閱  
 [try、throw 和 catch 陳述式 (C++)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [C++ 例外狀況處理](../cpp/cpp-exception-handling.md)
