---
title: 結構化例外狀況處理 （C/c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1edcf2cb24273f475b1ba98e5e973f5704c0cec8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461698"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)
雖然 Windows 和 Visual C++ 支援結構化例外狀況處理 (SEH)，但是建議您使用 ISO 標準 C++ 例外狀況處理，因為它可提升程式碼的可攜性和彈性。 儘管如此，在現有程式碼中或針對特定類型的程式，您仍然必須使用 SEH。  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
  
## <a name="grammar"></a>文法  
 *try 陳述式除了*:  
  
 `__try` *複合陳述式*  
  
 `__except` ( `expression` )*複合陳述式*  
  
## <a name="remarks"></a>備註  
 使用 SEH，您可以確定資源 (例如記憶體區塊和檔案) 在執行意外終止時正確。 您也可以處理特定問題 — 比方說，沒有足夠的記憶體 — 使用簡潔的結構化程式碼，不會依賴**goto**陳述式，或傳回碼的複雜測試。  
  
 本文中參照的 try-except 和 try-finally 陳述式是 C 語言的 Microsoft 擴充功能。 它們支援 SEH，讓應用程式在終止執行的事件之後取得程式的控制權。 雖然 SEH 與 C++ 原始程式檔搭配運作，但它不是專為 C++ 所設計。 如果您使用編譯的 c + + 程式中使用 SEH [/EH](../build/reference/eh-exception-handling-model.md)選項 — 與特定修飾詞，呼叫本機物件的解構函式，但其他執行行為可能不是您的預期。 (如需說明，請參閱本文稍後的範例。)在大部分情況下，而不是 SEH 我們建議您使用 ISO 標準[c + + 例外狀況處理](../cpp/try-throw-and-catch-statements-cpp.md)，Visual c + + 也支援。 使用 C++ 例外狀況處理，確保您的程式碼更具可攜性，而且您可以處理任何類型的例外狀況。  
  
 如果您的 C 模組使用 SEH，則可以將它們與使用 C++ 例外狀況處理的 C++ 模組混合使用。 如需資訊，請參閱[例外狀況處理差異](../cpp/exception-handling-differences.md)。  
  
 有兩種 SEH 機制：  
  
-   [例外狀況處理常式](../cpp/writing-an-exception-handler.md)，可回應或關閉例外狀況。  
  
-   [終止處理常式](../cpp/writing-a-termination-handler.md)，例外狀況會造成程式碼區塊中的終止時呼叫。  
  
 這兩種處理常式不同，但透過稱為「回溯堆疊」的處理序密切相關。 例外狀況發生時，Windows 會尋找目前作用的最近安裝例外狀況處理常式。 處理常式可以執行下列三項事項的其中一項：  
  
-   無法辨識例外狀況，並將控制權傳給其他處理常式。  
  
-   辨識例外狀況，但關閉它。  
  
-   辨識例外狀況，並處理它。  
  
 可辨識例外狀況的例外狀況處理常式可能不在例外狀況發生時正在執行的函式中。 在某些情況下，它可能在堆疊上更高的函式中。 目前執行中函式和堆疊框架上的所有其他函式都會終止。 在此過程中，堆疊是 「 回溯 」 堆疊; 亦即，本機變數的終止函式 — 除非**靜態**— 會從堆疊清除。  
  
 回溯堆疊時，作業系統會呼叫您為每個函式所撰寫的任何終止處理常式。 透過使用終止處理常式，您可以清除因異常終止而仍然保持開啟的資源。 如果您已經進入重要區段，則可以在終止處理常式中結束。 如果程式即將關閉，您可以執行其他環境維護工作 (例如關閉和移除暫存檔案)。  
  
 如需詳細資訊，請參閱:  
  
-   [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)  
  
-   [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)  
  
-   [在 C++ 中使用結構化例外狀況處理](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>範例  
 如前所述，如果您在 C++ 程式中使用 SEH，並且搭配使用 `/EH` 選項與特定修飾詞 (例如，`/EHsc` 和 `/EHa`) 進行編譯，則會呼叫區域物件的解構函式。 不過，如果您同時使用 C++ 例外狀況，則在執行期間的行為可能會不如預期。 下列範例示範這些行為差異。  
  
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
  
 如果您使用 **/EHsc**若要編譯此程式碼，但本機測試控制項`CPPEX`會未定義，沒有任何執行`TestClass`解構函式，則輸出看起來像這樣：  
  
```Output  
Triggering SEH exception  
Executing SEH __except block  
```  
  
 如果您使用 **/EHsc**編譯程式碼並`CPPEX`使用定義`/DCPPEX`（以便讓 c + + 例外狀況會擲回），則`TestClass`解構函式執行，並輸出看起來像這樣：  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 如果您使用 **/EHa**編譯的程式碼`TestClass`解構函式執行，不論是否擲回例外狀況使用`std::throw`或使用 SEH 來觸發例外狀況 (`CPPEX`或未定義)。 輸出顯示如下：  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](../build/reference/eh-exception-handling-model.md)。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [\<exception>](../standard-library/exception.md)   
 [錯誤和例外狀況處理](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [結構化的例外處理 (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)