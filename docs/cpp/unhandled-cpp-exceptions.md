---
title: 未處理的 C++ 例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: cd5ce722c5159041ba8fb0a4a41b942a1bd4614f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246056"
---
# <a name="unhandled-c-exceptions"></a>未處理的 C++ 例外狀況

If a matching handler (or ellipsis **catch** handler) cannot be found for the current exception, the predefined `terminate` run-time function is called. (You can also explicitly call `terminate` in any of your handlers.) The default action of `terminate` is to call `abort`. 如果您希望 `terminate` 在結束應用程式之前呼叫程式中的其他函式，請使用做為單一引數呼叫的函式名稱來呼叫 `set_terminate` 函式。 您可以隨時在程式中呼叫 `set_terminate`。 The `terminate` routine always calls the last function given as an argument to `set_terminate`.

## <a name="example"></a>範例

下列範例會擲回 `char *` 例外狀況，不過，其中並不包含任何指定攔截 `char *` 類型例外狀況的處理常式。 對 `set_terminate` 的呼叫會指示 `terminate` 呼叫 `term_func`。

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>Output

```Output
term_func was called by terminate.
```

`term_func` 函式應該終止程式或目前的執行緒，最好是透過呼叫 `exit` 的方式進行。 如果未如預期進行而傳回至呼叫端，則會呼叫 `abort`。

## <a name="see-also"></a>請參閱

[Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md)