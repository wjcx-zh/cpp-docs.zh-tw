---
title: try、throw 和 catch 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 4108d24b2c285b9d55d514dffae7b2efda1b3f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227058"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 陳述式 (C++)

若要在 c + + 中執行例外狀況處理，您可以使用 **`try`** 、 **`throw`** 和 **`catch`** 運算式。

首先，使用 **`try`** 區塊來括住一個或多個可能會擲回例外狀況的語句。

**`throw`** 運算式表示區塊中發生例外狀況（通常是錯誤） **`try`** 。 您可以使用任何類型的物件做為運算式的運算元 **`throw`** 。 這個物件通常用來傳達與錯誤有關的資訊。 在大部分情況下，我們建議您使用[std：： exception](../standard-library/exception-class.md)類別或在標準程式庫中定義的其中一個衍生類別。 如果有任何不適用的類別，建議您從 `std::exception` 自行衍生例外狀況類別。

若要處理可能擲回的例外狀況，請 **`catch`** 在區塊之後立即執行一或多個區塊 **`try`** 。 每個 **`catch`** 區塊會指定它可以處理的例外狀況類型。

這個範例會顯示 **`try`** 區塊和其處理常式。 假設 `GetNetworkResource()` 透過網路連線取得資料，且兩個例外狀況類型是衍生自 `std::exception` 的使用者定義類別。 請注意，語句中的參考會攔截到例外狀況 **`const`** **`catch`** 。 建議您依照值擲回例外狀況並依 const 參考攔截這些例外狀況。

## <a name="example"></a>範例

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>備註

子句之後的 **`try`** 程式碼是程式碼的保護區段。 **`throw`** 運算式會擲*回（* 也就是引發）例外狀況。 子句之後的程式碼區塊 **`catch`** 是例外狀況處理常式。 如果和運算式中的型別相容，這就是攔截擲回之例外*狀況的處理*程式 **`throw`** **`catch`** 。 如需在區塊中管理類型相符的規則清單 **`catch`** ，請參閱[如何評估 Catch 區塊](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果 **`catch`** 語句指定省略號（...），而不是類型，則 **`catch`** 區塊會處理每種類型的例外狀況。 當您使用[/eha](../build/reference/eh-exception-handling-model.md)選項進行編譯時，這些可能包括 C 結構化例外狀況和系統產生或應用程式產生的非同步例外狀況，例如記憶體保護、零除和浮點違規。 因為 **`catch`** 區塊會在程式順序中進行處理，以尋找相符的類型，所以省略號處理常式必須是相關聯區塊的最後一個處理常式 **`try`** 。 使用 `catch(...)` 時請小心；除非 catch 區塊知道如何處理所攔截到的特定例外狀況，否則不可允許程式繼續執行。 通常，`catch(...)` 區塊的用途是在程式停止執行之前記錄錯誤和執行特殊清除。

**`throw`** 沒有運算元的運算式會重新擲回目前正在處理的例外狀況。 重新擲回例外狀況時，建議使用此表單，因為其中保留了原始例外狀況的多型類型資訊。 這類運算式只能用在處理常式中 **`catch`** ，或是在從處理常式呼叫的函式中 **`catch`** 。 重新擲回的例外狀況物件是原始的例外狀況物件，而不是複本。

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>另請參閱

[適用于例外狀況和錯誤處理的新式 c + + 最佳作法](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[未處理的 c + + 例外](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
