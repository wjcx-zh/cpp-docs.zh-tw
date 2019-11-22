---
title: 字串和 I/O 格式化 (現代 C++)
description: 新式C++中提供的格式化字串 i/o 選項。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: facb0b62cc1e92ed09a9ba729d766e5db7404282
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74308172"
---
# <a name="string-and-io-formatting-modern-c"></a>字串和 I/O 格式化 (現代 C++)

C++[\<iostream >](../standard-library/iostream.md)類別、函數和運算子支援格式化的字串 i/o。 例如，下列程式碼會示範如何設定 `cout`，以將整數格式化為十六進位的輸出。 首先，它會儲存目前的狀態，以便在之後重設，因為一旦將狀態傳遞給 `cout`之後，它就會維持不變，直到變更為止。 它不只適用于一行程式碼。

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

這種方法是型別安全且可延伸，但也很複雜而且更冗長。

## <a name="alternative-format-options"></a>替代格式選項

或者，您也可以從提升C++程式庫使用 `Boost.Format`，即使它不是標準的也一樣。 您可以從[提升](https://www.boost.org/)的網站下載任何提升程式庫。

`Boost.Format` 的一些優點如下：

- Safe：型別安全，並擲回錯誤的例外狀況，例如，太少或太多專案的規格。

- 可擴充：適用于任何可進行資料流程處理的類型。

- 方便：標準 Posix 和類似的格式字串。

雖然 `Boost.Format` 是建置於C++安全且可擴充的[\<iostream >](../standard-library/iostream-programming.md)設備上，但它們不會優化效能。 當您需要效能優化時，請考慮 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，這是快速且容易使用的。 不過，它們不是可延伸或不安全的弱點。 （安全版本存在，但會造成些許效能的負面影響。 如需詳細資訊，請參閱[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)）。

下列程式碼示範一些增強格式設定功能。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>請參閱

[歡迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
