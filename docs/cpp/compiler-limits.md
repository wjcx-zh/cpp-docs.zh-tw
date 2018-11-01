---
title: 編譯器限制
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: a0c6041d326982dc9807355733cf714dcfa62ca8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600326"
---
# <a name="compiler-limits"></a>編譯器限制

C++ 標準會建議各種語言的建構限制。 下列是 Visual C++ 編譯器未實作所建議之限制的案例。 第一個數字是 ISO C++ 11 標準 (INCITS/ISO/IEC 14882-2011[2012], Annex B) 所建立的限制，第二個數字是 Visual C++ 所實作的限制：

- 巢狀層級的複合陳述式、 反覆項目控制結構及選取控制結構-c + + 標準： 256，Visual c + + 編譯器： 視陳述式的巢狀，但通常介於 100 和 110 之間的組合。

- 參數，一個在巨集定義中的 c + + 標準： 256，Visual c + + 編譯器： 127。

- 引數，在一個巨集引動過程-c + + 標準： 256，Visual c + + 編譯器： 127。

- 中字元的字元字串常值或寬字串常值 （串連之後）-c + + 標準： 65536，Visual c + + 編譯器： 65535 的單一位元組字元，包括 NULL 結束字元和 32767 雙位元組字元，包括 NULL 結束字元。

- 層級的巢狀的類別、 結構或等位定義單一`struct-declaration-list`-c + + 標準： 256，Visual c + + 編譯器： 16。

- 成員初始設定式中的建構函式定義為 c + + 標準： 6144，Visual c + + 編譯器： 至少 6144。

- 範圍限定性條件的識別碼-c + + 標準： 256，Visual c + + 編譯器： 127。

- 巢狀**extern**規格-c + + 標準： 1024，Visual c + + 編譯器： 9 (不計入隱含**extern**規格中，則為 10，如果您計算隱含**extern**規格在全域範圍中的...

- 樣板宣告-c + + 標準中的樣板引數： 1024，Visual c + + 編譯器： 2046年。

## <a name="see-also"></a>另請參閱

[非標準行為](../cpp/nonstandard-behavior.md)