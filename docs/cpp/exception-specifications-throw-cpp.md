---
title: 例外狀況規格 （throw、 noexcept） （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab09d5aadb489208b2e7591c2bf0f60ab836da4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417596"
---
# <a name="exception-specifications-throw-noexcept-c"></a>例外狀況規格 （throw、 noexcept） （c + +）

例外狀況規格是 c + + 語言功能，以指出例外狀況類型的函式進行傳播相關的程式設計人員的目的。 您可以指定函式可能會或可能不會結束例外狀況使用*例外狀況規格*。 編譯器可以使用這項資訊來最佳化呼叫函式，並以結束程式。 如果預期的例外狀況逸出函式。 

在 C + + 17 之前發生例外狀況規格的兩種。 *Noexcept 規格*是一項新的 C + + 11。 它會指定可能的例外狀況可以逸出函式的集合是否為空白。 *動態例外狀況規格*，或`throw(optional_type_list)`規格是 C + + 11 中已被取代，而且在 C + + 17，移除除了`throw()`，這是別名`noexcept(true)`。 此例外狀況規格設計來提供離函式，可以擲回例外狀況的摘要資訊，但實際上它找不到問題。 經過證明有些許用處一個動態例外狀況規格是無條件`throw()`規格。 例如，函式宣告：

```cpp
void MyFunction(int i) throw();
```
通知編譯器，函式不會擲回任何例外狀況。 不過，在 **/std:c + + 14**模式，這可能會導致未定義的行為如果函式並擲回例外狀況。 因此我們建議使用[noexcept](../cpp/noexcept-cpp.md)運算子，而不是上述其中一個：

```cpp
void MyFunction(int i) noexcept;
```
下表摘要說明 Microsoft Visual c + + 例外狀況規格實作：

|例外狀況規格|意義|
|-----------------------------|-------------|
|`noexcept`<br>`noexcept(true)`<br>`throw()`|函式不會擲回例外狀況。 在[/std:c + + 14](../build/reference/std-specify-language-standard-version.md)模式 （這是預設值），`noexcept`和`noexcept(true)`相等。 當擲回例外狀況宣告的函式從`noexcept`或`noexcept(true)`， [std:: terminate](../standard-library/exception-functions.md#terminate)叫用。 當從函式擲回例外狀況宣告為`throw()`中 **/std:c + + 14**模式中，結果是未定義的行為。 沒有特定的函式會叫用。 這是從 C + + 14 標準，其叫用編譯器時所需的歧異[std::unexpected](../standard-library/exception-functions.md#unexpected)。  <br> **Visual Studio 2017 15.5 和更新版本**： 在 **/std:c + + 17**模式中， `noexcept`， `noexcept(true)`，和`throw()`都是相等的。 在 **/std:c + + 17**模式中，`throw()`別名`noexcept(true)`。 在 **/std:c + + 17**模式中，從這些規格中宣告的函式擲回例外狀況時[std:: terminate](../standard-library/exception-functions.md#terminate)叫用的要求以 C + + 17 標準。|
|`noexcept(false)`<br/>`throw(...)`<br/>無規格|此函式會擲回任何類型的例外狀況。|
|`throw(type)`| (**C + + 14 和更早版本**) 函式可能擲回例外狀況型別的`type`。 編譯器會接受語法，但會將它做為解譯`noexcept(false)`。 在 **/std:c + + 17**模式下，編譯器會發出警告 C5040。|

如果應用程式中使用例外狀況處理，必須有函式擲回例外狀況之前離開函式的外部範圍的控點標示之呼叫堆疊中`noexcept`， `noexcept(true)`，或`throw()`。 如果任何函式呼叫之間會將所擲回例外狀況和處理例外狀況的一個指定為`noexcept`， `noexcept(true)` (或`throw()`中 **/std:c + + 17**模式)，則會終止程式時noexcept 函式會傳播例外狀況。

函式的例外狀況行為取決於下列因素：

- 其中[語言標準編譯模式](../build/reference/std-specify-language-standard-version.md)設定。
- 在 C 或 C++ 中編譯函式。

- 其中[/EH](../build/reference/eh-exception-handling-model.md)您使用的編譯器選項。

- 您是否明確指定例外狀況規格。

C 函式不允許明確例外狀況規格。 C 函式會假設不擲回例外狀況下的 **/EHsc**，可能會擲回下的結構化例外狀況和 **/EHs**， **/EHa**，或 **/EHac**。

下表摘要說明是否可能會在各種編譯器例外狀況處理選項可能會擲回 c + + 函式：

|功能|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|沒有例外狀況規格的 C++ 函式|[是]|是|是|[是]|
|具有 c + + 函式`noexcept`， `noexcept(true)`，或`throw()`例外狀況規格|否|否|是|[是]|
|具有 c + + 函式`noexcept(false)`， `throw(...)`，或`throw(type)`例外狀況規格|[是]|是|是|[是]|

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

 [再試一次、 throw 和 catch 陳述式 （c + +）](../cpp/try-throw-and-catch-statements-cpp.md) [c + + 例外狀況處理](../cpp/cpp-exception-handling.md)