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

如果找不到目前例外狀況的相符處理常式（或省略**catch**處理常式），則會呼叫預先定義的 `terminate` 執行時間函式。 （您也可以在任何處理程式中明確地呼叫 `terminate`）。`terminate` 的預設動作是呼叫 `abort`。 如果您希望 `terminate` 在結束應用程式之前呼叫程式中的其他函式，請使用做為單一引數呼叫的函式名稱來呼叫 `set_terminate` 函式。 您可以隨時在程式中呼叫 `set_terminate`。 `terminate` 常式一律會呼叫指定為引數的最後一個函式，以 `set_terminate`。

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

## <a name="output"></a>輸出

```Output
term_func was called by terminate.
```

`term_func` 函式應該終止程式或目前的執行緒，最好是透過呼叫 `exit` 的方式進行。 如果未如預期進行而傳回至呼叫端，則會呼叫 `abort`。

## <a name="see-also"></a>另請參閱

[例外C++狀況和錯誤處理的現代化最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)