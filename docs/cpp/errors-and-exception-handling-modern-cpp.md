---
title: 例外C++狀況和錯誤處理的現代化最佳做法
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: 85a8bf0f64681387cbee63f273fda5ce93ab7ad5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245872"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>例外C++狀況和錯誤處理的現代化最佳做法

在現代化C++中，在大多數情況下，最適合用來報告和處理邏輯錯誤和執行階段錯誤的方式，是使用例外狀況。 當堆疊可能包含偵測到錯誤的函式，以及具有內容以瞭解如何處理它的函式之間的多個函式呼叫時，更是如此。 例外狀況針對偵測錯誤的程式碼提供了正式且妥善定義的方式，以將資訊傳遞至呼叫堆疊。

程式錯誤通常分成兩個類別：因程式設計錯誤所造成的邏輯錯誤（例如「索引超出範圍」錯誤），以及不受程式設計師控制的執行階段錯誤，例如「網路服務無法使用」糾錯. 在 C 樣式程式設計和 COM 中，錯誤報表是藉由傳回代表特定函式的錯誤碼或狀態碼的值，或藉由設定呼叫者在每次函式呼叫之後可以選擇性抓取的全域變數來進行管理是否報告錯誤。 例如，COM 程式設計會使用 HRESULT 傳回值來傳達錯誤給呼叫端，而 WIN32 API 則具有 GetLastError 函式，可抓取呼叫堆疊所回報的最後一個錯誤。 在這兩種情況下，都是由呼叫者辨識程式碼並適當地回應。 如果呼叫端未明確處理錯誤碼，程式可能會在沒有警告的情況下損毀，或繼續以錯誤的資料執行，並產生不正確的結果。

基於下列原因，現代C++會偏好例外狀況：

- 例外狀況會強制呼叫程式碼來辨識錯誤條件並加以處理。 未處理的例外狀況會停止程式執行。

- 例外狀況會跳至呼叫堆疊中可處理錯誤的點。 中繼函數可以讓例外狀況傳播。 它們不需要與其他圖層協調。

- 例外狀況堆疊-回溯機制會在擲回例外狀況之後，根據妥善定義的規則，終結範圍中的所有物件。

- 例外狀況可讓偵測錯誤的程式碼和處理錯誤的程式碼之間有清楚的分隔。

下列簡化的範例顯示在中C++擲回和攔截例外狀況的必要語法。

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

中C++的例外狀況類似于C#和 JAVA 等語言。 在**try**區塊中，如果擲回例外*狀況，則會*由其類型符合例外狀況的第一個相關聯**catch**區塊攔截*到*。 換句話說，執行會從**throw**語句跳至**catch**語句。 如果找不到可用的 catch 區塊，則會叫用 `std::terminate` 並結束程式。 在C++中，可能會擲回任何類型;不過，我們建議您擲回直接或間接衍生自 `std::exception`的類型。 在上述範例中，例外狀況類型（ [invalid_argument](../standard-library/invalid-argument-class.md)）定義于[\<stdexcept> >](../standard-library/stdexcept.md)標頭檔的標準程式庫中。 C++不提供，而且不需要**finally**區塊，以確保在擲回例外狀況時釋放所有資源。 資源取得是使用智慧型指標的初始化（RAII）用法，可提供資源清除所需的功能。 如需詳細資訊，請參閱[如何：針對例外狀況安全性進行設計](how-to-design-for-exception-safety.md)。 如需C++堆疊回溯機制的詳細資訊，請參閱[例外狀況和堆疊](exceptions-and-stack-unwinding-in-cpp.md)回溯。

## <a name="basic-guidelines"></a>基本指導方針

健全的錯誤處理是任何程式設計語言中的挑戰。 雖然例外狀況提供了數個支援良好錯誤處理的功能，但無法為您執行所有工作。 若要實現例外狀況機制的優點，請在設計程式碼時記住例外狀況。

- 使用判斷提示來檢查永遠不會發生的錯誤。 使用例外狀況來檢查可能發生的錯誤，例如，公用函式參數上的輸入驗證錯誤。 如需詳細資訊，請參閱標題**例外狀況與判斷**提示一節。

- 當處理錯誤的程式碼與透過一或多個中間函式呼叫偵測到錯誤的程式碼分開時，請使用例外狀況。 當處理錯誤的程式碼緊密結合到偵測到它的程式碼時，請考慮是否要改用錯誤碼，而不是在效能關鍵迴圈中使用。

- 針對每個可能擲回或傳播例外狀況的函式，提供下列三個例外狀況保證之一：強式保證、基本保證，或 nothrow （noexcept）保證。 如需詳細資訊，請參閱[如何：針對例外狀況安全性進行設計](how-to-design-for-exception-safety.md)。

- 依值擲回例外狀況，並以傳址方式加以攔截。 請勿攔截您無法處理的內容。

- 請勿使用在 c + + 11 中已被取代的例外狀況規格。 如需詳細資訊，請參閱 >例外狀況規格和 noexcept一節。

- 適用時，請使用標準程式庫例外狀況類型。 從[Exception 類別](../standard-library/exception-class.md)階層衍生自訂例外狀況類型。

- 不允許例外狀況從析構函數或記憶體解除配置函式中進行 escape。

## <a name="exceptions-and-performance"></a>例外狀況和效能

如果沒有擲回例外狀況，則例外狀況機制的效能會非常最低。 如果擲回例外狀況，則堆疊遍歷和回溯的成本大致上與函式呼叫的成本比較。 在輸入**try**區塊之後，需要額外的資料結構來追蹤呼叫堆疊，如果擲回例外狀況，則需要其他指示來回溯堆疊。 不過，在大部分的情況下，效能和記憶體使用量的成本並不重要。 對於效能例外狀況的負面影響，可能只有在記憶體受限的系統上，或在效能關鍵的迴圈中，可能會定期發生錯誤，且處理常式代碼與報告它的程式碼緊密結合。 在任何情況下，不可能知道例外狀況的實際成本，而不需要分析和測量。 即使在這種罕見的情況下，當成本很高時，您也可以將其與設計良好的例外狀況原則所提供的更佳正確性、更容易維護性和其他優點加以權衡。

## <a name="exceptions-vs-assertions"></a>例外狀況與判斷提示

例外狀況和判斷提示是用來偵測程式中執行階段錯誤的兩個不同機制。 在開發期間，如果您的所有程式碼都正確，請使用判斷提示來測試條件。 由於錯誤指出程式碼中的某個專案必須固定，而不代表程式必須在執行時間復原的條件，因此不會使用例外狀況來處理這類錯誤。 判斷提示會在語句停止執行，讓您可以在偵錯工具中檢查程式狀態。例外狀況會從第一個適當的 catch 處理常式繼續執行。 使用例外狀況來檢查在執行時間可能發生的錯誤情況，即使您的程式碼是正確的，例如「找不到檔案」或「記憶體不足」。 即使復原只會將訊息輸出到記錄檔並結束程式，您仍可能想要從這些狀況中復原。 請一律使用例外狀況來檢查公用函式的引數。 即使您的函式是無錯誤的，您可能無法完全控制使用者可能會傳遞給它的引數。

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C++例外狀況與 Windows SEH 例外狀況

C 和C++程式都可以在 Windows 作業系統中使用結構化例外狀況處理（SEH）機制。 SEH 中C++的概念類似于例外狀況，但 seh 使用 **__try**、 **__except**和 **__finally**結構，而不是**try**和**catch**。 在 Microsoft C++編譯器（MSVC）中， C++會針對 SEH 執行例外狀況。 不過，當您撰寫C++程式碼時， C++請使用例外狀況語法。

如需 SEH 的詳細資訊，請參閱[結構化例外狀況C++處理（C/）](structured-exception-handling-c-cpp.md)。

## <a name="exception-specifications-and-noexcept"></a>例外狀況規格和 noexcept

中C++引進了例外狀況規格，以指定函式可能會擲回的例外狀況。 不過，例外狀況規格在實務上已證明有問題，並已在 c + + 11 草稿標準中被取代。 我們建議您不要使用例外狀況規格，但 `throw()`除外，這表示函式不允許任何例外狀況來進行 escape。 如果您必須使用類型的例外狀況規格 `throw(`*類型*`)`，請注意，MSVC 會以特定方式從標準離開。 如需詳細資訊，請參閱[例外狀況規格（throw）](exception-specifications-throw-cpp.md)。 `noexcept` 規範會在 c + + 11 中引進，做為 `throw()`的慣用替代方式。

## <a name="see-also"></a>另請參閱

[如何：例外狀況和非例外狀況代碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
