---
title: 編譯器限制
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: e0e2381d88c727466b06a97c72826d2d5e15a87b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233765"
---
# <a name="compiler-limits"></a>編譯器限制

C++ 標準會建議各種語言的建構限制。 以下是 Microsoft c + + 編譯器不會執行建議限制的案例清單。 第一個數位是 ISO c + + 11 標準（INCITS/ISO/IEC 14882-2011 [2012]，附錄 B）中所建立的限制，而第二個數字則是 Microsoft c + + 編譯器所執行的限制：

- 複合陳述式、反復專案控制結構和選取控制結構的嵌套層級-c + + 標準：256、Microsoft c + + 編譯器：取決於嵌套的語句組合，但通常是在100與110之間。

- 一個巨集定義中的參數-c + + 標準：256、Microsoft c + + 編譯器：127。

- 一個宏調用中的引數-c + + 標準：256、Microsoft c + + 編譯器127。

- 字元字串常值或寬字元串常值中的字元（在串連之後）-c + + 標準：65536、Microsoft c + + 編譯器：65535單一位元組字元（包括 Null 結束字元）和32767雙位元組字元，包括 Null 結束字元。

- 單一 c + + 標準中的嵌套類別、結構或等位定義層級 `struct-declaration-list` ：256、Microsoft c + + 編譯器：16。

- 在函式定義中的成員初始化運算式-c + + 標準：6144、Microsoft c + + 編譯器：至少6144。

- 一個識別碼的範圍限定-c + + 標準：256、Microsoft c + + 編譯器：127。

- 嵌套 **`extern`** 規格-c + + 標準：1024、Microsoft c + + 編譯器：9（ **`extern`** 如果您在全域範圍中計算隱含規格，則不會計算全域範圍中的隱含規格，或10） **`extern`** 。

- 範本宣告中的樣板引數-c + + 標準：1024、Microsoft c + + 編譯器：2046。

## <a name="see-also"></a>另請參閱

[非標準行為](../cpp/nonstandard-behavior.md)
