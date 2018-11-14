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
ms.openlocfilehash: a55c1f2d5c2e73028b337d17b74fe1280f670707
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326702"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw 和 catch 陳述式 (C++)

若要實作的 c + + 例外狀況處理，您使用**嘗試**，**擲回**，並**攔截**運算式。

首先，使用**嘗試**區塊包含可能會擲回例外狀況的一或多個陳述式。

A**擲回**運算式表示的例外狀況，通常是錯誤 — 中發生**嘗試**區塊。 您可以使用任何類型的物件作為運算元**擲回**運算式。 這個物件通常用來傳達與錯誤有關的資訊。 在大部分情況下，我們建議您使用[std:: exception](../standard-library/exception-class.md)類別或其中一個衍生類別中的標準程式庫所定義。 如果有任何不適用的類別，建議您從 `std::exception` 自行衍生例外狀況類別。

若要處理可能會擲回的例外狀況，實作一或多個**攔截**區塊之後緊接著**嘗試**區塊。 每個**攔截**區塊指定它可以處理的例外狀況類型。

此範例示範**嘗試**區塊和其處理常式。 假設 `GetNetworkResource()` 透過網路連線取得資料，且兩個例外狀況類型是衍生自 `std::exception` 的使用者定義類別。 請注意，例外狀況所捕捉**const**參考中**攔截**陳述式。 建議您依照值擲回例外狀況並依 const 參考攔截這些例外狀況。

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

後面的程式碼**嘗試**子句是程式碼的保護的區段。 **擲回**運算式*就會擲回*— 也就是引發，例外狀況。 之後的程式碼區塊**攔截**子句是例外狀況處理常式。 這個處理常式，*攔截*便會擲回的例外狀況中的型別**擲回**並**攔截**運算式都相容。 如需管理中的型別符合規則的清單**攔截**區塊，請參閱[如何 Catch 區塊的評估](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果**攔截**陳述式指定省略符號 （...） 而不是類型，**攔截**區塊處理的例外狀況的每個型別。 當您編譯[/EHa](../build/reference/eh-exception-handling-model.md)選項，這些可能包括 C 結構化例外狀況和系統產生或應用程式所產生的非同步例外，例如記憶體保護、 除以-零和浮點違規. 因為**攔截**區塊會處理程式的順序，找不到相符的類型、 省略符號處理常式必須是最後一個處理常式相關聯**嘗試**區塊。 使用 `catch(...)` 時請小心；除非 catch 區塊知道如何處理所攔截到的特定例外狀況，否則不可允許程式繼續執行。 通常，`catch(...)` 區塊的用途是在程式停止執行之前記錄錯誤和執行特殊清除。

A**擲回**不含運算元的運算式會重新擲回目前正在處理的例外狀況。 重新擲回例外狀況時，建議使用此表單，因為其中保留了原始例外狀況的多型類型資訊。 這類運算式只能在**攔截**處理常式或從呼叫的函式**攔截**處理常式。 重新擲回的例外狀況物件是原始的例外狀況物件，而不是複本。

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

[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[未處理的 C++ 例外狀況](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)