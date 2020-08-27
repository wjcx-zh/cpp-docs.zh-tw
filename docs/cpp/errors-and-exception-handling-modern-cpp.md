---
title: 適用于例外狀況和錯誤處理的新式 c + + 最佳作法
description: 現代 c + + 如何針對錯誤碼支援異常程式設計樣式。
ms.date: 08/24/2020
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: b402c93ea5af3cc7dab418b6dea58446ae300c67
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898368"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>適用于例外狀況和錯誤處理的新式 c + + 最佳作法

在現代 c + + 中，在大部分情況下，報告和處理邏輯錯誤和執行階段錯誤的慣用方式是使用例外狀況。 尤其是當堆疊可能在偵測到錯誤的函式之間包含數個函式呼叫，以及有內容可處理錯誤的函式時，更是如此。 例外狀況會針對偵測錯誤的程式碼提供正式且妥善定義的方法，以將資訊傳遞至呼叫堆疊。

## <a name="use-exceptions-for-exceptional-code"></a>在例外狀況程式碼中使用例外狀況

程式錯誤通常分為兩種類別：程式設計錯誤所造成的邏輯錯誤，例如「索引超出範圍」錯誤。 和程式設計人員的控制權以外的執行階段錯誤，例如「網路服務無法使用」錯誤。 在 C 樣式程式設計和 COM 中，錯誤報表的管理方式是藉由傳回代表特定函式的錯誤碼或狀態碼的值，或是設定呼叫端在每次函式呼叫之後可選擇性地取出的全域變數，以查看是否已回報錯誤。 例如，COM 程式設計會使用 HRESULT 傳回值，將錯誤傳達給呼叫者。 和 WIN32 API 具有函式， `GetLastError` 可取得由呼叫堆疊回報的最後一個錯誤。 在這兩種情況下，由呼叫端負責辨識程式碼並適當地回應。 如果呼叫端未明確處理錯誤碼，則程式可能會損毀，而不會發出警告。 或者，它可能會繼續使用不正確的資料執行，並產生不正確的結果。

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

C + + 中的例外狀況類似于 c # 和 JAVA 等語言的例外狀況。 在區塊中，如果擲回例外狀況，則會 **`try`** 由類型符合例外狀況的*thrown*第一個關聯區塊*捕捉* **`catch`** 。 換句話說，執行會從 **`throw`** 語句跳至 **`catch`** 語句。 如果找不到可使用的 catch 區塊， `std::terminate` 則會叫用並結束程式。 在 c + + 中，可能會擲回任何類型;不過，我們建議您擲回直接或間接衍生的型別 `std::exception` 。 在上述範例中，例外狀況類型 [`invalid_argument`](../standard-library/invalid-argument-class.md) 是在標頭檔的標準程式庫中定義 [`<stdexcept>`](../standard-library/stdexcept.md) 。 C + + 不會提供或要求 **`finally`** 區塊，以確保在擲回例外狀況時釋放所有資源。 資源取得是 (RAII 的初始化) 使用智慧型指標的用法，提供資源清除所需的功能。 如需詳細資訊，請參閱 [如何：設計例外狀況安全性](how-to-design-for-exception-safety.md)。 如需 c + + 堆疊回溯機制的詳細資訊，請參閱 [例外狀況和堆疊](exceptions-and-stack-unwinding-in-cpp.md)回溯。

## <a name="basic-guidelines"></a>基本指導方針

在任何程式設計語言中，健全的錯誤處理是一項挑戰。 雖然例外狀況提供數個支援良好錯誤處理的功能，但無法為您執行所有工作。 若要實現例外狀況機制的優點，請在設計程式碼時記住例外狀況。

- 使用判斷提示來檢查應該永遠不會發生的錯誤。 使用例外狀況來檢查可能發生的錯誤，例如，在公用函式的參數上輸入驗證的錯誤。 如需詳細資訊，請參閱 [例外狀況與判斷](#exceptions_versus_assertions) 提示一節。

- 當處理錯誤的程式碼與透過一或多個中間函式呼叫偵測錯誤的程式碼分開時，請使用例外狀況。 當處理錯誤的程式碼與偵測到錯誤的程式碼緊密結合時，請考慮是否要在效能關鍵迴圈中使用錯誤碼。

- 針對可能會擲回或傳播例外狀況的每個函式，提供三種例外狀況保證之一：強式保證、基本保證或 nothrow (noexcept) 保證。 如需詳細資訊，請參閱 [如何：設計例外狀況安全性](how-to-design-for-exception-safety.md)。

- 依值擲回例外狀況，以傳址方式攔截例外狀況。 請勿攔截您無法處理的內容。

- 請勿使用在 c + + 11 中已淘汰的例外狀況規格。 如需詳細資訊，請參閱[例外狀況 `noexcept` 規格和](#exception_specifications_and_noexcept)一節。

- 適用時，請使用標準程式庫例外狀況類型。 從[ `exception` 類別](../standard-library/exception-class.md)階層衍生自訂例外狀況類型。

- 不允許從析構函數或記憶體解除配置函式進行 escape 的例外狀況。

## <a name="exceptions-and-performance"></a>例外狀況和效能

如果沒有擲回例外狀況，則例外狀況機制會有最基本的效能成本。 如果擲回例外狀況，堆疊遍歷和回溯的成本大致上相當於函式呼叫的成本。 輸入區塊之後，需要額外的資料結構來追蹤呼叫堆疊 **`try`** ，而如果擲回例外狀況，則需要其他指示來回溯堆疊。 不過，在大部分情況下，效能和記憶體使用量的成本並不重要。 例外狀況對效能的負面影響，可能只有在記憶體受限的系統上才有意義。 或者，在效能關鍵的迴圈中，錯誤可能會定期發生，而且程式碼與處理它的程式碼之間有緊密的聯繫性。 在任何情況下，不可能知道例外狀況的實際成本，而不需要進行分析和測量。 即使在這種罕見的情況下，成本是很重要的，您也可以將它與設計完善的例外狀況原則所提供的更高正確性、更容易維護性以及其他優點進行權衡。

## <a name="exceptions-versus-assertions"></a><a name="exceptions_versus_assertions"></a> 例外狀況與判斷提示

例外狀況和判斷提示是兩種不同的機制，用來偵測程式中的執行階段錯誤。 `assert`如果您的所有程式碼都是正確的，請使用語句在開發期間測試條件，而不應該為 true。 由於錯誤指出程式碼中的某個內容必須固定，因此不會使用例外狀況來處理這類錯誤。 它不代表程式必須在執行時間復原的條件。 `assert`會在語句中停止執行，如此您就可以在偵錯工具中檢查程式狀態。 例外狀況會從第一個適當的 catch 處理常式繼續執行。 使用例外狀況來檢查可能在執行時間發生的錯誤狀況，即使您的程式碼正確，例如「找不到檔案」或「記憶體不足」。 例外狀況可以處理這些情況，即使復原只是將訊息輸出到記錄檔並結束程式。 請一律使用例外狀況檢查公用函式的引數。 即使您的函式是無錯誤的，您可能無法完全控制使用者可能傳遞給它的引數。

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C + + 例外狀況與 Windows SEH 例外狀況

C 和 c + + 程式都可以在 Windows 作業系統中使用結構化例外狀況處理 (SEH) 機制。 SEH 中的概念與 c + + 例外狀況中的概念類似，不同之處在于 SEH 會使用 **`__try`** 、 **`__except`** 和 **`__finally`** 結構，而不是 **`try`** 和 **`catch`** 。 在 Microsoft c + + 編譯器 (MSVC) 中，c + + 例外狀況是針對 SEH 所執行。 但是，當您撰寫 c + + 程式碼時，請使用 c + + 例外狀況語法。

如需 SEH 的詳細資訊，請參閱 [結構化例外狀況處理 (C/c + +) ](structured-exception-handling-c-cpp.md)。

## <a name="exception-specifications-and-noexcept"></a><a name="exception_specifications_and_noexcept"></a> 例外狀況規格和 `noexcept`

例外狀況規格在 c + + 中是以指定函式可能擲回之例外狀況的方式來引進。 不過，例外狀況規格在實務上已證明有問題，並已在 c + + 11 草稿標準中淘汰。 我們建議您不要使用 **`throw`** 以外的例外狀況規格 `throw()` ，這表示函式不允許任何例外狀況進行 escape。 如果您必須使用已被取代之表單的例外狀況規格 `throw( type-name )` ，MSVC 支援受限。 如需詳細資訊，請參閱 [例外狀況規格 (擲回) ](exception-specifications-throw-cpp.md)。 **`noexcept`** 規範是在 c + + 11 中引進，做為的慣用替代方法 `throw()` 。

## <a name="see-also"></a>請參閱

[如何：例外狀況和非例外狀況程式碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
