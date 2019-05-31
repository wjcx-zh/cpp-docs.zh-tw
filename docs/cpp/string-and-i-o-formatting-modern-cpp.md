---
title: 字串和 I/O 格式化 (現代 C++)
description: 在現代化的格式化字串可用的 I/O 選項C++。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: e22c745798109a2dbef82297c45256593823f806
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450496"
---
# <a name="string-and-io-formatting-modern-c"></a>字串和 I/O 格式化 (現代 C++)

C++[ \<iostream >](../standard-library/iostream.md)類別、 函數和運算子支援格式化的字串 I/O。 例如，下列程式碼示範如何設定`cout`格式化輸出以十六進位表示的整數。 首先，它會將儲存之後，重設目前的狀態傳遞給格式狀態一次，因為`cout`，它會保持這種方式直到變更為止。 它不會直接套用以一行程式碼。

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

這個方法的型別安全和擴充性，但也很複雜而詳細。

## <a name="alternative-format-options"></a>替代格式選項

或者，您可以使用`Boost.Format`提升從C++程式庫，即使它是非標準。 您可以下載任何 Boost 程式庫，從[Boost](https://www.boost.org/)網站。

一些優點`Boost.Format`是：

- 安全：類型安全，並擲回例外狀況的錯誤，比方說，太少或太多的項目規格。

- 可延伸：適用於串流處理任何類型。

- 方便：標準 Posix 和類似的格式字串。

雖然`Boost.Format`建基於C++ [ \<iostream >](../standard-library/iostream-programming.md)功能，也就是安全且可擴充，它們不是效能最佳化。 當您需要效能最佳化時，請考慮使用 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)並[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，這是快速且容易使用。 不過，它們不是可延伸或安全性弱點。 （安全版本存在，但它們會造成些微的效能損失。 如需詳細資訊，請參閱 < [printf_s、 _printf_s_l、 wprintf_s、 _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)並[sprintf_s、 _sprintf_s_l、 swprintf_s、 _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md))。

下列程式碼會示範部分提升格式化功能。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>另請參閱

[歡迎回到 C++ (現代 C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
