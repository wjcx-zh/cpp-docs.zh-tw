---
title: 適用于例外狀況和錯誤處理的新式 c + + 最佳作法
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: 6995867813bfb65848f179cb56b358de68fa63f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227526"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>適用于例外狀況和錯誤處理的新式 c + + 最佳作法

在現代 c + + 中，在大部分情況下，報告和處理邏輯錯誤和執行階段錯誤的慣用方式是使用例外狀況。 當堆疊可能會在偵測到錯誤的函式，以及具有內容的函式知道如何處理它的函式之間包含數個函式呼叫時，更是如此。 例外狀況會針對偵測錯誤的程式碼提供正式且妥善定義的方法，以將資訊傳遞至呼叫堆疊。

程式錯誤通常分為兩種類別：程式設計錯誤所造成的邏輯錯誤，例如「索引超出範圍」錯誤，以及不受程式設計人員控制的執行階段錯誤，例如「網路服務無法使用」錯誤。 在 C 樣式程式設計和 COM 中，錯誤報表的管理方式是藉由傳回代表特定函式的錯誤碼或狀態碼的值，或是設定呼叫端在每次函式呼叫之後可選擇性地取出的全域變數，以查看是否已回報錯誤。 例如，COM 程式設計會使用 HRESULT 傳回值將錯誤傳達給呼叫端，而 WIN32 API 則具有 GetLastError 函式，可取得由呼叫堆疊回報的最後一個錯誤。 在這兩種情況下，由呼叫端負責辨識程式碼並適當地回應。 如果呼叫端未明確處理錯誤碼，則程式可能會在沒有警告的情況下損毀，或繼續以不正確的資料執行，並產生不正確的結果。

現代 c + + 中偏好例外狀況的原因如下：

- 例外狀況會強制呼叫程式碼辨識錯誤狀況並加以處理。 未處理的例外狀況會停止程式執行。

- 例外狀況會跳到可處理錯誤的呼叫堆疊中的點。 中繼函數可讓例外狀況傳播。 它們不需要與其他圖層協調。

- 例外狀況堆疊回溯機制會在擲回例外狀況之後，根據妥善定義的規則終結範圍中的所有物件。

- 例外狀況可讓偵測錯誤的程式碼和處理錯誤的程式碼之間有清楚的分隔。

下列簡化的範例顯示在 c + + 中擲回和捕捉例外狀況的必要語法。

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

C + + 中的例外狀況類似于 c # 和 JAVA 等語言的例外狀況。 在區塊中，如果擲回例外狀況，則會 **`try`** 由類型符合例外狀況的*thrown*第一個關聯區塊*捕捉* **`catch`** 。 換句話說，執行會從 **`throw`** 語句跳至 **`catch`** 語句。 如果找不到可使用的 catch 區塊， `std::terminate` 則會叫用並結束程式。 在 c + + 中，可能會擲回任何類型;不過，我們建議您擲回直接或間接衍生的型別 `std::exception` 。 在上述範例中，會在標頭檔的標準程式庫中定義例外狀況類型（ [invalid_argument](../standard-library/invalid-argument-class.md)） [\<stdexcept>](../standard-library/stdexcept.md) 。 如果擲回例外狀況，c + + 不會提供並不需要 **finally** 區塊，以確保釋放所有資源。 資源取得是 (RAII 的初始化) 使用智慧型指標的用法，提供資源清除所需的功能。 如需詳細資訊，請參閱 [如何：設計例外狀況安全性](how-to-design-for-exception-safety.md)。 如需 c + + 堆疊回溯機制的詳細資訊，請參閱 [例外狀況和堆疊](exceptions-and-stack-unwinding-in-cpp.md)回溯。

## <a name="basic-guidelines"></a>基本指導方針

在任何程式設計語言中，健全的錯誤處理是一項挑戰。 雖然例外狀況提供數個支援良好錯誤處理的功能，但無法為您執行所有工作。 若要實現例外狀況機制的優點，請在設計程式碼時記住例外狀況。

- 使用判斷提示來檢查應該永遠不會發生的錯誤。 使用例外狀況來檢查可能發生的錯誤，例如，在公用函式的參數上輸入驗證的錯誤。 如需詳細資訊，請參閱標題為 **例外狀況與判斷**提示的區段。

- 當處理錯誤的程式碼可能與透過一或多個中間函式呼叫偵測錯誤的程式碼分開時，請使用例外狀況。 當處理錯誤的程式碼與偵測到此錯誤的程式碼緊密結合時，請考慮是否要在效能關鍵迴圈中改用錯誤碼。

- 針對可能會擲回或傳播例外狀況的每個函式，提供三種例外狀況保證之一：強式保證、基本保證或 nothrow (noexcept) 保證。 如需詳細資訊，請參閱 [如何：設計例外狀況安全性](how-to-design-for-exception-safety.md)。

- 依值擲回例外狀況，以傳址方式攔截例外狀況。 請勿攔截您無法處理的內容。

- 請勿使用在 c + + 11 中已淘汰的例外狀況規格。 如需詳細資訊，請參閱標題為 **例外狀況規格和 noexcept**一節。

- 適用時，請使用標準程式庫例外狀況類型。 從 [例外狀況類別](../standard-library/exception-class.md) 階層衍生自訂例外狀況類型。

- 不允許從析構函數或記憶體解除配置函式進行 escape 的例外狀況。

## <a name="exceptions-and-performance"></a>例外狀況和效能

如果沒有擲回例外狀況，則例外狀況機制的效能成本非常低。 如果擲回例外狀況，堆疊遍歷和回溯的成本大致上相當於函式呼叫的成本。 輸入區塊之後，需要額外的資料結構來追蹤呼叫堆疊 **`try`** ，而如果擲回例外狀況，則需要其他指示來回溯堆疊。 不過，在大部分情況下，效能和記憶體使用量的成本並不重要。 在效能上，例外狀況的負面影響可能只有在非常記憶體限制的系統上，或在可能會定期發生錯誤的效能關鍵迴圈中，以及處理它的程式碼與報告該錯誤的程式碼緊密結合的情況下很重要。 在任何情況下，不可能知道例外狀況的實際成本，而不需要進行分析和測量。 即使在這種罕見的情況下，成本是很重要的，您也可以將它與設計完善的例外狀況原則所提供的更高正確性、更容易維護性以及其他優點進行權衡。

## <a name="exceptions-vs-assertions"></a>例外狀況與判斷提示

例外狀況和判斷提示是兩種不同的機制，用來偵測程式中的執行階段錯誤。 使用判斷提示，在開發期間測試條件，如果您的所有程式碼都正確，則永遠不會是 true。 由於錯誤指出程式碼中的某個專案必須固定，且不代表程式必須在執行時間復原的條件，因此不會使用例外狀況來處理這類錯誤。 判斷提示會在語句停止執行，如此您就可以在偵錯工具中檢查程式狀態。例外狀況會從第一個適當的 catch 處理常式繼續執行。 使用例外狀況來檢查可能在執行時間發生的錯誤狀況，即使您的程式碼正確，例如「找不到檔案」或「記憶體不足」。 您可能會想要從這些狀況中復原，即使復原只是將訊息輸出到記錄檔並結束程式。 請一律使用例外狀況檢查公用函式的引數。 即使您的函式是無錯誤的，您可能無法完全控制使用者可能傳遞給它的引數。

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C + + 例外狀況與 Windows SEH 例外狀況

C 和 c + + 程式都可以在 Windows 作業系統中使用結構化例外狀況處理 (SEH) 機制。 SEH 中的概念與 c + + 例外狀況中的概念類似，但 SEH 會使用 **__try**、 **`__except`** 和 **`__finally`** 結構，而不是 **`try`** 和 **`catch`** 。 在 Microsoft c + + 編譯器 (MSVC) 中，c + + 例外狀況是針對 SEH 所執行。 但是，當您撰寫 c + + 程式碼時，請使用 c + + 例外狀況語法。

如需 SEH 的詳細資訊，請參閱 [結構化例外狀況處理 (C/c + +) ](structured-exception-handling-c-cpp.md)。

## <a name="exception-specifications-and-noexcept"></a>例外狀況規格和 noexcept

例外狀況規格在 c + + 中是以指定函式可能擲回之例外狀況的方式來引進。 不過，例外狀況規格在實務上已證明有問題，並已在 c + + 11 草稿標準中淘汰。 我們建議您不要使用例外狀況規格，除了以外 `throw()` ，這表示函式不允許任何例外狀況進行 escape。 如果您必須使用類型類型的例外狀況規格 `throw(` *type* `)` ，請注意，MSVC 會以特定方式從標準離開。 如需詳細資訊，請參閱 [例外狀況規格 (擲回) ](exception-specifications-throw-cpp.md)。 **`noexcept`** 規範是在 c + + 11 中引進，做為的慣用替代方法 `throw()` 。

## <a name="see-also"></a>另請參閱

[如何：例外狀況和非例外狀況程式碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
