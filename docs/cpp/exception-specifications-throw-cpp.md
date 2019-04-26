---
title: 例外狀況規格 （throw、 noexcept） (C++)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 9280f3d96088d988a9d5cfe0f3d56444b865167e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154330"
---
# <a name="exception-specifications-throw-noexcept-c"></a>例外狀況規格 （throw、 noexcept） (C++)

例外狀況規格是C++語言功能，指出例外狀況相關的程式設計人員的目的型別可以傳播函式。 您可以指定函式可能會或可能不會結束例外狀況使用*例外狀況規格*。 編譯器可以使用這項資訊來最佳化呼叫函式，並終止程式，如果預期的例外狀況逸出的函式。

在 c++17 之前發生兩種類型的例外狀況規格。 *Noexcept 規格*的新功能 C + + 11。 它會指定可能的例外狀況可以逸出的函式的集合是否為空白。 *動態例外狀況規格*，或`throw(optional_type_list)`規格，是在 c++11 中已被取代，而且在 c++17 中，移除，除了`throw()`，這是別名`noexcept(true)`。 此例外狀況規格已設計成提供從函式，可以擲回什麼例外狀況的摘要資訊，但實際上它找到有問題。 證明有些許用處的一個動態例外狀況規格是無條件`throw()`規格。 例如，函式宣告：

```cpp
void MyFunction(int i) throw();
```
通知編譯器，函式不會擲回任何例外狀況。 不過，在 **/std: c + + 14**模式，這可能會導致未定義行為，如果函式會擲回例外狀況。 因此我們建議您使用[noexcept](../cpp/noexcept-cpp.md)運算子來取代上述其中一個：

```cpp
void MyFunction(int i) noexcept;
```
下表摘要說明 Microsoft VisualC++例外狀況規格實作：

|例外狀況規格|意義|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|函式不會擲回例外狀況。 在[/std: c + + 14](../build/reference/std-specify-language-standard-version.md)模式 （這是預設值），`noexcept`和`noexcept(true)`相等。 當從宣告的函式擲回例外狀況`noexcept`或是`noexcept(true)`， [std:: terminate](../standard-library/exception-functions.md#terminate)叫用。 當從函式擲回例外狀況宣告為`throw()`中 **/std: c + + 14**模式中，結果是未定義的行為。 沒有任何特定的函式會叫用。 這是從 C + + 14 標準，其叫用編譯器時所需的歧異[std::unexpected](../standard-library/exception-functions.md#unexpected)。  <br/> **Visual Studio 2017 15.5 版和更新版本**:在  **/std: c + + 17**模式中， `noexcept`， `noexcept(true)`，和`throw()`都是相等的。 在  **/std: c + + 17**模式中，`throw()`為其別名`noexcept(true)`。 在  **/std: c + + 17**模式中，從這些規格中的任何宣告的函式擲回例外狀況時[std:: terminate](../standard-library/exception-functions.md#terminate)叫用 C + + 17 標準所需。|
|`noexcept(false)`<br/>`throw(...)`<br/>無規格|此函式可以擲回任何類型的例外狀況。|
|`throw(type)`| (**C + + 14 和更早版本**) 的函式可能會擲回例外狀況型別的`type`。 編譯器會接受語法，但會將它做為解譯`noexcept(false)`。 在  **/std: c + + 17**模式下，編譯器會發出警告 C5040。|

如果應用程式中使用例外狀況處理，必須有函式中擲回例外狀況，才能在離開函式的外部範圍的控制代碼標示的呼叫堆疊`noexcept`， `noexcept(true)`，或`throw()`。 如果呼叫之間的任何函式會將會擲回例外狀況，以及處理例外狀況指定為`noexcept`， `noexcept(true)` (或`throw()`中 **/std: c + + 17**模式)，則會終止程式時noexcept 函式會傳播例外狀況。

函式的例外狀況行為取決於下列因素：

- 這[語言標準編譯模式](../build/reference/std-specify-language-standard-version.md)設定。
- 在 C 或 C++ 中編譯函式。

- 這[/EH](../build/reference/eh-exception-handling-model.md)您所使用的編譯器選項。

- 您是否明確指定例外狀況規格。

C 函式不允許明確例外狀況規格。 C 函式會假設不擲回例外狀況下的 **/EHsc**，並可能會在結構化例外狀況擲回 **/EHs**， **/EHa**，或 **/EHac**。

下表摘要說明是否C++可能會在各種不同的編譯器例外狀況處理的選項可能會擲回函式：

|功能|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|沒有例外狀況規格的 C++ 函式|是|是|是|是|
|C++函式搭配`noexcept`， `noexcept(true)`，或`throw()`例外狀況規格|否|否|是|是|
|C++函式搭配`noexcept(false)`， `throw(...)`，或`throw(type)`例外狀況規格|是|是|是|是|

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

[try、throw 和 catch 陳述式 (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)