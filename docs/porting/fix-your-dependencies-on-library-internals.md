---
title: 修正程式庫內部項目上的相依性 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e72e6b5e3fdfdb352d908b2fb9d0609593e7c2
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820921"
---
# <a name="fix-your-dependencies-on-library-internals"></a>修正程式庫內部項目上的相依性

Microsoft 已在許多 Visual Studio 版本中，發佈標準程式庫、大部分 C 執行階段程式庫，以及其他 Microsoft 程式庫的原始程式碼。 旨在協助您了解程式庫行為和偵錯程式碼。 發佈程式庫原始程式碼的副作用之一，是會公開某些內部值、資料結構和函式，即使它們不是程式庫介面的一部分。 它們的名稱開頭通常是兩個底線或底線後面接著一個大寫字母，C++ 標準保留要實作的名稱。 這些值、結構和函式是實作詳細資料，會隨著程式庫與時進化而變更，因此強烈建議您不要對其建立任何相依性。 如果這樣做，當您嘗試將程式碼移轉至新版程式庫時，就可能發生程式碼不可攜帶和其他問題。

多數情況下，Visual Studio 各版本的新功能或重大變更文件，不會提及程式庫內部項目的變更。 畢竟，您本來就不應該受到這些實作細節所影響。 只不過，有時候在程式庫內看到程式碼，想要使用的誘惑實在太大。 本主題討論您可能依存的 CRT 或標準程式庫內部項目相依性，以及如何更新程式碼以移除這些相依性，以便更容易攜帶或遷移至新版的程式庫。

## <a name="hashseq"></a>_Hash_seq

最近幾版的標準程式庫中，都可見到內部雜湊函式 `std::_Hash_seq(const unsigned char *, size_t)`，用來對某些字串類型實作 `std::hash`。 此函式在字元序列上實作了 [FNV-1a 雜湊]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function)。

您有幾個方法可以移除此相依性。

- 如果您打算使用和 `basic_string` 相同的雜湊程式碼機制，將 `const char *` 序列放入未排序的容器，您可以使用採用 `std::string_view` 的 `std::hash` 範本多載執行此動作，它會以可攜帶的方式傳回雜湊程式碼。 字串程式庫程式碼未來可能會、也可能不會依賴使用 FNV-1a 雜湊，因此這是避免對特定雜湊演算法產生相依性的最佳方式。

- 如果您打算在任意記憶體上產生 FNV-1a 雜湊，我們已在 GitHub 上提供該程式碼：位在 [MIT 授權](https://github.com/Microsoft/VCSamples/blob/master/license.txt)下，獨立標頭檔 [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq) 的 [VCSamples]( https://github.com/Microsoft/vcsamples) 儲存機制中。 這裡也收錄複本，方便您參考。 您可以將此程式碼複製到標頭檔，將標頭新增至任何受影響的程式碼，然後用 `fnv1a_hash_bytes` 尋找和取代 `_Hash_seq`。 您會得到和 `_Hash_seq` 的內部實作相同的行為。

```cpp
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved.
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;
#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>另請參閱

[從舊版的 Visual C++ 升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[潛在升級問題概觀 (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[將程式碼升級至通用 CRT](upgrade-your-code-to-the-universal-crt.md)  