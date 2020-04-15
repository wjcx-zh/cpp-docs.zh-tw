---
title: 字串和 I/O 格式化 (現代 C++)
description: 格式化字串 I/O 的選擇在現代C++中可用。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375778"
---
# <a name="string-and-io-formatting-modern-c"></a>字串和 I/O 格式化 (現代 C++)

C++ [ \<iostream>](../standard-library/iostream.md)類、函數和運算支援格式化的字串 I/O。 例如,以下代碼演示如何設置`cout`以十六進位形式輸出的整數格式。 首先,它保存當前狀態以在之後重置它,因為一旦格式狀態傳遞給`cout`,它將一直保持這種狀態,直到更改。 它不僅僅適用於一行代碼。

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

此方法類型安全且可擴展,但它也複雜而詳細。

## <a name="alternative-format-options"></a>選擇性的格式選項

作為替代方法,您可以使用`Boost.Format`Boost C++庫,即使它不標準。 您可以從 Boost 網站下載任何[Boost](https://www.boost.org/)庫。

一些優點`Boost.Format`是:

- 安全:類型安全,並引發錯誤的異常,例如,規格太少或太多項。

- 可擴展:適用於任何可以流式傳輸的類型。

- 方便:標準 POSIX 和類似的格式字串。

雖然`Boost.Format`基於C++[\<物聯網>](../standard-library/iostream-programming.md)設施,這些設施是安全和可擴展的,但它們沒有經過性能優化。 當您需要性能優化時,請考慮 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf,](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)它們快速且易於使用。 但是,它們不能擴展或免受漏洞的攻擊。 (存在安全版本,但它們會受到輕微的性能損失。 有關詳細資訊,請參閱[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l。](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)

以下代碼演示了一些 Boost 格式設置功能。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>另請參閱

[歡迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++語言參考](../cpp/cpp-language-reference.md)<br/>
[C++標準庫](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<限制>](../standard-library/limits.md)<br/>
[\<奧馬尼普>](../standard-library/iomanip.md)
