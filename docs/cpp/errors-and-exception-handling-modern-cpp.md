---
title: 錯誤和例外狀況處理 (現代 C++)
ms.date: 09/17/2018
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: c3def77d8b7a22be05259784e3b80562c8728c15
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220565"
---
# <a name="errors-and-exception-handling-modern-c"></a>錯誤和例外狀況處理 (現代 C++)

在現代 c + +，在大部分情況下，報告和處理邏輯錯誤和執行階段錯誤的慣用的方法是使用例外狀況。 堆疊可能包含數個函式呼叫之間偵測到錯誤的函式和函式具有要知道如何處理它的內容時，這是特別有用。 例外狀況會提供正式、 明確定義方法的程式碼來偵測錯誤的呼叫堆疊資訊傳遞出去。

程式錯誤通常分為兩類： 邏輯錯誤所造成程式設計錯誤，例如，「 索引超出範圍 」 錯誤，而執行階段錯誤，例如所控制的程式設計師而言，「 網路服務無法使用 」發生錯誤。 傳回值，表示錯誤碼或狀態碼為特定的函式，或設定全域變數，以查看每個函式呼叫後選擇性擷取呼叫端在 c-style 程式設計和 COM 中，管理錯誤報告是否發生錯誤。 例如，COM 程式設計使用來傳達給呼叫者，錯誤的 HRESULT 傳回值，而 Win32 API 有 GetLastError 函式來擷取最後一個呼叫堆疊報告的錯誤。 在這兩種情況下，它是可辨識的程式碼，並適當地回應，讓呼叫端。 如果呼叫端未明確處理的錯誤程式碼，程式可能會損毀，而不發出警告，或繼續執行正確的資料和產生不正確的結果。

例外狀況是現代 c + + 中慣用的原因如下：

- 例外狀況會強制呼叫程式碼辨識錯誤狀況，並處理。 未處理例外狀況停止程式執行。

- 例外狀況跳至可以處理錯誤的呼叫堆疊中的點。 中繼函式可以讓例外狀況傳播。 它們沒有協調與其他層級。

- 例外狀況堆疊回溯機制會終結根據妥善定義的規則的範圍內的所有物件之後擲回例外狀況。

- 例外狀況可讓您偵測到錯誤的程式碼和處理錯誤的程式碼之間清楚的分隔。

下列簡化的範例顯示擲回和攔截 c + + 中的例外狀況所需的語法。

```cpp

#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}
```

C + + 中的例外狀況類似 C# 和 Java 等語言中。 中**嘗試**例外狀況是如果封鎖*擲回*會*攔截*之第一個相關聯**攔截**其類型符合該區塊例外狀況。 換句話說，執行會從跳**擲回**陳述式來**攔截**陳述式。 如果找不到任何可用的 catch 區塊，`std::terminate`叫用並結束程式。 在 c + +，任何型別可能會擲回;不過，我們建議您擲回直接或間接衍生自類型`std::exception`。 在上一個範例中，例外狀況型別[invalid_argument](../standard-library/invalid-argument-class.md)中的標準程式庫中定義[ \<stdexcept> >](../standard-library/stdexcept.md)標頭檔。 C + + 不提供，而且不需要，**最後**區塊以確保如果發生例外狀況時釋放所有資源。 「 資源擷取是初始化 (RAII) 慣用語，其使用智慧型指標，提供必要的功能資源清除。 如需詳細資訊，請參閱[＜How to：例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。 如需 c + + 堆疊回溯機制的資訊，請參閱[例外狀況和堆疊回溯](../cpp/exceptions-and-stack-unwinding-in-cpp.md)。

## <a name="basic-guidelines"></a>基本的指導方針

強固的錯誤處理是一項挑戰，以任何程式設計語言。 例外狀況提供支援適當錯誤處理的幾項功能，但它們不能為您來執行所有工作。 若要實現例外狀況機制的優點，例外狀況納入考量，當您設計您的程式碼。

- 使用判斷提示檢查有應該永遠不會發生的錯誤。 您可以使用例外狀況，檢查有可能發生的錯誤，例如，輸入驗證參數的公用函式中的錯誤。 如需詳細資訊，請參閱下一節**例外狀況與。判斷提示**。

- 當處理錯誤的程式碼可能會從偵測到錯誤的程式碼分隔一或多個中間函式呼叫時，請使用例外狀況。 請考慮是否要改用錯誤碼重要效能迴圈中時處理錯誤的程式碼會偵測到它的程式碼緊密結合。

- 針對每個函式可能擲回或傳播例外狀況，提供三個例外狀況保證之一： 強式保證、 基本保證或 nothrow (noexcept) 保證。 如需詳細資訊，請參閱[＜How to：例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。

- 值，所擲回例外狀況，攔截它們的參考。 不會攔截您無法處理。

- 不要使用例外狀況規格在 c++11 中已被取代。 如需詳細資訊，請參閱下一節**例外狀況規格和 noexcept**。

- 套用時，請使用標準程式庫例外狀況類型。 衍生自訂例外狀況類型從[exception 類別](../standard-library/exception-class.md)階層。

- 不允許例外狀況從解構函式逸出或記憶體解除配置函式。

## <a name="exceptions-and-performance"></a>例外狀況和效能

例外狀況機制有極小的效能成本在擲回任何例外狀況。 如果擲回例外狀況，成本，堆疊周遊和回溯是大概相當於在函式呼叫成本。 其他資料結構，才能追蹤之後的呼叫堆疊**嘗試**進入區塊時，以及其他指示，才能在擲回例外狀況時回溯堆疊。 不過，在大部分情況下，在效能和記憶體耗用量成本並不重要。 例外狀況對效能的不利的影響很可能是重大只在記憶體非常受限的系統，或在效能關鍵執行迴圈錯誤很可能會定期執行，而處理它的程式碼緊密結合的程式碼報告它。 在任何情況下，就無法知道例外狀況的實際成本，而不需要程式碼剖析和測量。 即使在這些極少數的情況下時成本很重要，您可以衡量其根據增加的正確性、 更容易維護性，以及其他設計完善的例外狀況原則所提供的優點。

## <a name="exceptions-vs-assertions"></a>例外狀況與判斷提示的比較

例外狀況和判斷提示會在程式中偵測到執行階段錯誤的兩個不同機制。 使用判斷提示，不應為 true，如果您的程式碼是正確的開發期間，測試條件。 沒有任何點在處理這類錯誤就使用例外狀況，因為此錯誤表示在程式碼中的項目，必須加以修正，並不代表程式必須在執行階段從復原的條件。 判斷提示會停止執行的陳述式，因此您可以檢查偵錯工具; 中的程式狀態例外狀況會繼續執行，從第一個適當的 catch 處理常式。 使用例外狀況檢查可能發生在執行階段中，即使您的程式碼是正確的比方說，「 找不到檔案 」 或 「 記憶體不足。 」 的錯誤狀況 您可能想要復原這些情況中，即使復原只是將訊息輸出至記錄檔，並結束程式。 使用例外狀況，一律檢查公用函式的引數。 即使您的函式是無錯誤，您可能沒有使用者可能會傳遞給它的引數的完整控制權。

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>與 Windows SEH 例外狀況的 c + + 例外狀況

C 和 c + + 程式可以使用結構化例外狀況處理 (SEH) 機制，在 Windows 作業系統中。 SEH 的概念類似 c + + 例外狀況，不同之處在於會使用 SEH **__try**， **__except**，並 **__finally**而不是建構**嘗試**並**攔截**。 Visual c + +，c + + 例外狀況是針對 SEH 實作。 不過，當您撰寫 c + + 程式碼時，使用 c + + 例外狀況語法。

如需 SEH 的詳細資訊，請參閱[Structured Exception Handling （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)。

## <a name="exception-specifications-and-noexcept"></a>例外狀況規格和 noexcept

例外狀況規格在 c + + 中導入做為指定的函式可能擲回的例外狀況的方式。 不過，例外狀況規格經證實實務上，有問題，而在 c++11 草稿標準中已被取代。 我們建議您不要使用例外狀況規格，除了`throw()`，表示函式可讓任何例外狀況逸出。 如果您必須使用類型的例外狀況規格`throw(`*型別*`)`，注意 Visual c + + 偏離標準所規定的方式。 如需詳細資訊，請參閱 <<c0> [ 例外狀況規格 (throw)](../cpp/exception-specifications-throw-cpp.md)。 `noexcept`規範 C + + 11 中導入做為慣用的替代方案`throw()`。

## <a name="see-also"></a>另請參閱

[如何：例外狀況和非例外狀況代碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[歡迎回到 C++ (現代 C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
