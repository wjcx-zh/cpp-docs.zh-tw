---
title: 編譯器錯誤 C2707
ms.date: 11/04/2016
f1_keywords:
- C2707
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
ms.openlocfilehash: ce86f69b36b915b3e757b5d18430c99cb288e4e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648171"
---
# <a name="compiler-error-c2707"></a>編譯器錯誤 C2707

'identifier': 內建函式不正確的內容

結構化例外狀況處理的內建函式是在特定內容中無效：

- `_exception_code()` 外部例外狀況篩選條件或`__except`區塊

- `_exception_info()` 外部例外狀況篩選條件

- `_abnormal_termination()` 外部`__finally`區塊

若要解決此錯誤，請確定例外狀況處理內建函式會放在適當的內容。

## <a name="example"></a>範例

下列範例會產生 C2707。

```
// C2707.cpp
#include <windows.h>
#include <stdio.h>

LONG MyFilter(LONG excode)
{
    return (excode == EXCEPTION_ACCESS_VIOLATION ?
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK
}

LONG func(void)
{
    int x, y;
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);

    __try
    {
        y = 0;
        x = 4 / y;
        return 0;
     }

    __except(MyFilter(GetExceptionCode()))
    {
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);
    }
}

int main()
{
    __try
    {
        func();
    } __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf_s("Caught exception\n");
    }
}
```