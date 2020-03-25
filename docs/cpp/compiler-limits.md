---
title: 編譯器限制
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189571"
---
# <a name="compiler-limits"></a>編譯器限制

C++ 標準會建議各種語言的建構限制。 以下是 Microsoft C++編譯器不會執行建議限制的案例清單。 第一個數位是 ISO C++ 11 標準（INCITS/ISO/IEC 14882-2011 [2012]，附錄 B）中所建立的限制，而第二個數字是 Microsoft C++編譯器所實行的限制：

- 複合陳述式、反復專案控制結構和選取控制結構的嵌套層級C++ -標準：256、 C++ Microsoft 編譯器：取決於嵌套的語句組合，但通常是在100與110之間。

- 一個巨集定義中的參數- C++標準：256、Microsoft C++編譯器：127。

- 一個宏調用中的自C++變數-標準： 256 C++ 、Microsoft 編譯器127。

- 字元字串常值或寬字元串常值中的字元（在串連C++之後）-標準： C++ 65536、Microsoft 編譯器：65535單位元組字元，包括 null 結束字元和32767雙位元組字元，包括 null 結束字元。

- 單一 `struct-declaration-list` 標準中的嵌套類別、結構或等位C++定義層級：256、Microsoft C++編譯器：16。

- 在函式定義中的成員初始化C++運算式-標準： 6144 C++ 、Microsoft 編譯器：至少6144。

- 一個識別碼的範圍限定C++標準：256、Microsoft C++編譯器：127。

- Nested **extern**規格- C++標準：1024、Microsoft C++編譯器：9（不計算全域範圍中的隱含**外部**規格，或10，如果您在全域範圍中計算隱含**外部**規格。

- 範本宣告中的樣板引數C++ -標準：1024、 C++ Microsoft 編譯器：2046。

## <a name="see-also"></a>另請參閱

[非標準行為](../cpp/nonstandard-behavior.md)
