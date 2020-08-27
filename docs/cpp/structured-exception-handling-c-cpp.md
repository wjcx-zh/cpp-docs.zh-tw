---
title: Structured Exception Handling (C/C++)
description: Microsoft C/c + + 中結構化例外狀況處理的總覽。
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 142e89bc82adbe7938e8825029908e814df6055c
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898626"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

結構化例外狀況處理 (SEH) 是 Microsoft 的 C 延伸模組，可正常地處理特定的異常程式碼情況，例如硬體錯誤。 雖然 Windows 和 Microsoft c + + 支援 SEH，但是建議您使用 ISO 標準 c + + 例外狀況處理。 它讓您的程式碼更具可攜性和彈性。 不過，若要維護現有的程式碼或特定種類的程式，您仍然必須使用 SEH。

**Microsoft 專用：**

## <a name="grammar"></a>文法

> *`try-except-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__except`** **`(`** *`expression`* **`)`** *`compound-statement`*
>
> *`try-finally-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

## <a name="remarks"></a>備註

使用 SEH，您可以確保資源（例如記憶體區塊和檔案）會在執行意外終止時正確釋放。 您也可以使用不依賴語句的簡潔結構化程式碼 **`goto`** 或更精細的傳回碼測試，來處理特定問題（例如，記憶體不足）。

本文 `try-except` `try-finally` 中參考的和語句是 C 語言的 Microsoft 擴充功能。 它們支援 SEH，讓應用程式在終止執行的事件之後取得程式的控制權。 雖然 SEH 與 C++ 原始程式檔搭配運作，但它不是專為 C++ 所設計。 如果您在使用[ `/EHa` 或 `/EHsc` ](../build/reference/eh-exception-handling-model.md)選項編譯的 c + + 程式中使用 SEH，則會呼叫本機物件的析構程式，但其他執行行為可能不是您預期的行為。 如需圖例，請參閱本文稍後的範例。 在大部分的情況下，我們建議您不要使用 Microsoft c + + 編譯器也支援的 ISO 標準 [c + + 例外狀況處理](../cpp/try-throw-and-catch-statements-cpp.md)，而不是 SEH。 使用 C++ 例外狀況處理，確保您的程式碼更具可攜性，而且您可以處理任何類型的例外狀況。

如果您有使用 SEH 的 C 程式碼，您可以將它與使用 c + + 例外狀況處理的 c + + 程式碼混合使用。 如需詳細資訊，請參閱 [在 c + + 處理結構化例外](../cpp/exception-handling-differences.md)狀況。

有兩種 SEH 機制：

- [例外狀況處理常式](../cpp/writing-an-exception-handler.md)或 **`__except`** 區塊，可回應或關閉例外狀況。

- [終止處理常式](../cpp/writing-a-termination-handler.md)或 **`__finally`** 一律會呼叫的區塊，不論例外狀況是否會導致終止。

這兩種處理常式不同，但會透過稱為回溯 *堆疊*的進程密切相關。 當結構化例外狀況發生時，Windows 會尋找目前作用中的最近安裝的例外狀況處理常式。 處理常式可以執行下列三項事項的其中一項：

- 無法辨識例外狀況，並將控制權傳給其他處理常式。

- 辨識例外狀況，但關閉它。

- 辨識例外狀況，並處理它。

可辨識例外狀況的例外狀況處理常式可能不在例外狀況發生時正在執行的函式中。 它可能在堆疊上的函式中更高。 目前執行中函式和堆疊框架上的所有其他函式都會終止。 在此程式期間，會將堆疊 *展開*。 也就是說，已終止函式的區域非靜態變數會從堆疊中清除。

回溯堆疊時，作業系統會呼叫您為每個函式所撰寫的任何終止處理常式。 藉由使用終止處理常式，您可以清除資源，否則會因為異常終止而維持開啟。 如果您已輸入重要區段，您可以在終止處理常式中結束它。 當程式即將關閉時，您可以進行其他的維護工作，例如關閉和移除暫存檔案。

## <a name="next-steps"></a>後續步驟

- [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)

- [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)

- [使用 C++ 處理結構化例外狀況](../cpp/exception-handling-differences.md)

## <a name="example"></a>範例

如先前所述，如果您在 c + + 程式中使用 SEH 並使用或選項進行編譯，則會呼叫本機物件的析構函數 **`/EHa`** **`/EHsc`** 。 但是，如果您也使用 c + + 例外狀況，執行期間的行為可能不是您預期的行為。 此範例示範這些行為差異。

```cpp
#include <stdio.h>
#include <Windows.h>
#include <exception>

class TestClass
{
public:
    ~TestClass()
    {
        printf("Destroying TestClass!\r\n");
    }
};

__declspec(noinline) void TestCPPEX()
{
#ifdef CPPEX
    printf("Throwing C++ exception\r\n");
    throw std::exception("");
#else
    printf("Triggering SEH exception\r\n");
    volatile int *pInt = 0x00000000;
    *pInt = 20;
#endif
}

__declspec(noinline) void TestExceptions()
{
    TestClass d;
    TestCPPEX();
}

int main()
{
    __try
    {
        TestExceptions();
    }
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf("Executing SEH __except block\r\n");
    }

    return 0;
}
```

如果您使用 **`/EHsc`** 來編譯此程式碼，但未定義本機測試控制程式宏 `CPPEX` ，則 `TestClass` 不會執行此函式。 輸出如下所示：

```Output
Triggering SEH exception
Executing SEH __except block
```

如果您使用 **`/EHsc`** 來編譯器代碼，並 `CPPEX` 使用 (來定義，以便擲回 `/DCPPEX` c + + 例外狀況) ，則會 `TestClass` 執行此函式，而且輸出看起來像這樣：

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

如果您使用 **`/EHa`** 來編譯器代碼，則會使用 `TestClass` `std::throw` 或使用 SEH 來觸發例外狀況，來執行此函式的擲回例外狀況。 亦即，是否已 `CPPEX` 定義。 輸出如下所示：

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

如需詳細資訊，請參閱[ `/EH` (例外狀況處理模型) ](../build/reference/eh-exception-handling-model.md)。

**結束 Microsoft 專用**

## <a name="see-also"></a>請參閱

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[`<exception>`](../standard-library/exception.md)<br/>
[錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[ (Windows) 的結構化例外狀況處理 ](/windows/win32/debug/structured-exception-handling)
