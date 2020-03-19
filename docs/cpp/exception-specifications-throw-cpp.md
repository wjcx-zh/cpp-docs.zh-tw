---
title: 例外狀況規格（throw，noexcept）C++（）
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 4c7cc6027a3af4c300b88389cb29e3ccf091514e
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509404"
---
# <a name="exception-specifications-throw-noexcept-c"></a>例外狀況規格（throw，noexcept）C++（）

例外狀況規格是C++一種語言功能，指出程式設計人員對於可透過函式傳播的例外狀況類型的意圖。 您可以使用*例外狀況規格*，指定函式不一定是由例外狀況結束。 編譯器可以使用這種資訊來優化對函式的呼叫，並在發生未預期的例外狀況時，終止程式。

在 c + + 17 之前，有兩種例外狀況規格。 *Noexcept 規格*是 c + + 11 的新功能。 它會指定是否可以對函式進行轉義的可能例外狀況集合是空的。 *動態例外狀況規格*（或 `throw(optional_type_list)` 規格）在 c + + 11 中已被取代，並已在 c + + 17 中移除，但 `throw()`除外，這是 `noexcept(true)`的別名。 這個例外狀況規格的設計，是為了提供有關可從函式擲出哪些例外狀況的摘要資訊，但實際上卻發現問題。 其中一項動態例外狀況規格證明，特別有用的是無條件 `throw()` 規格。 例如，函式宣告：

```cpp
void MyFunction(int i) throw();
```

通知編譯器，函式不會擲回任何例外狀況。 不過，在 **/std： c + + 14**模式中，如果函式擲回例外狀況，這可能會導致未定義的行為。 因此，我們建議使用[noexcept](../cpp/noexcept-cpp.md)運算子，而不是上述各項：

```cpp
void MyFunction(int i) noexcept;
```

下表摘要說明「Microsoft C++的例外狀況規格」的執行方式：

|例外狀況規格|意義|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|函式不會擲回例外狀況。 在[/std 中： c + + 14](../build/reference/std-specify-language-standard-version.md)模式（這是預設值），`noexcept` 和 `noexcept(true)` 是相等的。 當從宣告 `noexcept` 或 `noexcept(true)`的函式擲回例外狀況時，會叫用[std：： terminate](../standard-library/exception-functions.md#terminate) 。 當 **/std： c + + 14**模式中宣告為 `throw()` 的函式擲回例外狀況時，結果會是未定義的行為。 不會叫用特定的函式。 這是與 c + + 14 標準的分歧，因此編譯器必須叫用[std：：非預期](../standard-library/exception-functions.md#unexpected)的。  <br/> **Visual Studio 2017 15.5 版和更新**版本：在 **/std： c + + 17**模式中，`noexcept`、`noexcept(true)`和 `throw()` 都是相等的。 在 **/std： c + + 17**模式中，`throw()` 是 `noexcept(true)`的別名。 在 **/std： c + + 17**模式中，從使用任何這些規格所宣告的函式擲回例外狀況時，會叫用 c + + 17 標準所需的[std：： terminate](../standard-library/exception-functions.md#terminate) 。|
|`noexcept(false)`<br/>`throw(...)`<br/>無規格|函式可能會擲回任何類型的例外狀況。|
|`throw(type)`| （**C + + 14 和更早版本**）函式可能會擲回 `type`類型的例外狀況。 編譯器會接受語法，但會將它解讀為 `noexcept(false)`。 在 **/std： c + + 17**模式中，編譯器會發出 warning C5040。|

如果在應用程式中使用例外狀況處理，則呼叫堆疊中必須有一個函式，該函式會在結束標記為 `noexcept`、`noexcept(true)`或 `throw()`之函式的外部範圍之前，處理擲回的例外狀況。 如果在擲回例外狀況的函式和處理例外狀況的函數之間呼叫的任何函式指定為 `noexcept`，`noexcept(true)` （或在 **/std： c + + 17**模式中 `throw()`），則程式會在 noexcept 函數傳播例外狀況時終止。

函式的例外狀況行為取決於下列因素：

- 設定的[語言標準編譯模式](../build/reference/std-specify-language-standard-version.md)。
- 在 C 或 C++ 中編譯函式。

- 您使用的[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項。

- 您是否明確指定例外狀況規格。

C 函式不允許明確例外狀況規格。 假設 C 函數不會在 **/ehsc**下擲回例外狀況，而且可能會在 **/ehs**、 **/eha**或 **/EHac**下擲回結構化例外狀況。

下表摘要說明函式C++是否可能會在各種編譯器例外狀況處理選項下擲回：

|函數|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|沒有例外狀況規格的 C++ 函式|是|是|是|是|
|C++具有 `noexcept`、`noexcept(true)`或 `throw()` 例外狀況規格的函式|否|否|是|是|
|C++具有 `noexcept(false)`、`throw(...)`或 `throw(type)` 例外狀況規格的函式|是|是|是|是|

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
[例外C++狀況和錯誤處理的現代化最佳做法](errors-and-exception-handling-modern-cpp.md)