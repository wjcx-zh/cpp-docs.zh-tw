---
title: Structured Exception Handling (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 942a7e48e4315454476bfe93c68169f461b006b2
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245121"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

結構化例外狀況處理（SEH）是 C 的 Microsoft 擴充功能，可正常處理特定的異常程式碼情況，例如硬體錯誤。 雖然 Windows 和 Microsoft C++支援 SEH，但建議您使用 ISO 標準C++的例外狀況處理，因為它可讓您的程式碼更具可攜性和彈性。 不過，若要維護現有的程式碼或特定類型的程式，您仍然可能必須使用 SEH。

**Microsoft 特定：**

## <a name="grammar"></a>文法

*try-except-語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *複合陳述式* **__except** **（** *expression* **）** *複合陳述式*

*try-catch-finally 語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *複合陳述式* **__finally** *複合陳述式*

## <a name="remarks"></a>備註

使用 SEH，您可以確保在執行意外終止時，會正確地釋放記憶體區塊和檔案之類的資源。 您也可以使用不依賴**goto**語句的簡潔結構化程式碼，或對傳回碼進行詳細測試，來處理特定問題（例如，記憶體不足）。

本文中參照的 try-except 和 try-finally 陳述式是 C 語言的 Microsoft 擴充功能。 它們支援 SEH，讓應用程式在終止執行的事件之後取得程式的控制權。 雖然 SEH 與 C++ 原始程式檔搭配運作，但它不是專為 C++ 所設計。 如果您在使用C++ [/eha 或/ehsc](../build/reference/eh-exception-handling-model.md)選項編譯的程式中使用 SEH，則會呼叫本機物件的析構函數，但其他執行行為可能不是您預期的結果。 如需說明，請參閱本文稍後的範例。 在大部分的情況下，我們建議您使用 Microsoft C++編譯器也支援的 ISO 標準[ C++例外狀況處理](../cpp/try-throw-and-catch-statements-cpp.md)，而不是 SEH。 使用 C++ 例外狀況處理，確保您的程式碼更具可攜性，而且您可以處理任何類型的例外狀況。

如果您有使用 SEH 的 C 程式碼，您可以將它C++與使用C++例外狀況處理的程式碼混合。 如需相關資訊，請參閱[處理C++中的結構化例外](../cpp/exception-handling-differences.md)狀況。

有兩種 SEH 機制：

- [例外狀況處理常式](../cpp/writing-an-exception-handler.md)或 **__except**區塊，可以回應或關閉例外狀況。

- [終止處理常式](../cpp/writing-a-termination-handler.md)或 **__finally**區塊（一律會呼叫），不論例外狀況是否導致終止。

這兩種處理常式不同，但透過稱為「回溯堆疊」的處理序密切相關。 當發生結構化例外狀況時，Windows 會尋找最近安裝的例外處理常式（目前為作用中）。 處理常式可以執行下列三項事項的其中一項：

- 無法辨識例外狀況，並將控制權傳給其他處理常式。

- 辨識例外狀況，但關閉它。

- 辨識例外狀況，並處理它。

可辨識例外狀況的例外狀況處理常式可能不在例外狀況發生時正在執行的函式中。 在某些情況下，它可能在堆疊上更高的函式中。 目前執行中函式和堆疊框架上的所有其他函式都會終止。 在此過程中，堆疊會「展開」，也就是說，已終止函式的本機非靜態變數會從堆疊中清除。

回溯堆疊時，作業系統會呼叫您為每個函式所撰寫的任何終止處理常式。 透過使用終止處理常式，您可以清除因異常終止而仍然保持開啟的資源。 如果您已輸入重要區段，您可以在終止處理常式中結束它。 如果程式即將關閉，您可以執行其他環境維護工作 (例如關閉和移除暫存檔案)。

## <a name="next-steps"></a>後續步驟

- [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)

- [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)

- [使用 C++ 處理結構化例外狀況](../cpp/exception-handling-differences.md)

## <a name="example"></a>範例

如先前所述，如果您在C++程式中使用 SEH，並使用 **/eha**或 **/ehsc**選項進行編譯，則會呼叫本機物件的析構函數。 不過，如果您同時使用 C++ 例外狀況，則在執行期間的行為可能會不如預期。 這個範例會示範這些行為差異。

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

如果您使用 **/ehsc**來編譯此程式碼，但未定義本機測試控制項宏 `CPPEX`，則不會執行 `TestClass` 的析構函式，而且輸出看起來會像這樣：

```Output
Triggering SEH exception
Executing SEH __except block
```

如果您使用 **/ehsc**來編譯器代碼，而且 `CPPEX` 是使用 `/DCPPEX` 定義的（因此會擲C++回例外狀況），則 `TestClass` 的析構函式會執行，且輸出看起來會像這樣：

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

如果您使用 **/eha**來編譯器代碼，無論是使用 `std::throw` 還是藉由使用 SEH 來觸發例外狀況（也就是是否 `CPPEX` 定義），都會執行 `TestClass` 的析構函式。 輸出顯示如下：

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

如需詳細資訊，請參閱 [/EH (Exception Handling Model)](../build/reference/eh-exception-handling-model.md)。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
[錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[結構化例外狀況處理（Windows）](/windows/win32/debug/structured-exception-handling)
