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
ms.openlocfilehash: 85227e0bd0ca33f925e8fe72b6489fa81305d031
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312206"
---
# <a name="unhandled-c-exceptions"></a>未處理的 C++ 例外狀況

如果相符的處理常式 (或省略符號**攔截**處理常式) 找不到目前的例外狀況，預先定義的`terminate`呼叫執行階段函式。 (您可以在任何處理常式中明確呼叫 `terminate`)。`terminate` 的預設動作是呼叫 `abort`。 如果您希望 `terminate` 在結束應用程式之前呼叫程式中的其他函式，請使用做為單一引數呼叫的函式名稱來呼叫 `set_terminate` 函式。 您可以隨時在程式中呼叫 `set_terminate`。 `terminate`常式會一律呼叫指定的引數為最後一個函式`set_terminate`。

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

## <a name="see-also"></a>另請參閱

[C++ 例外狀況處理](../cpp/cpp-exception-handling.md)