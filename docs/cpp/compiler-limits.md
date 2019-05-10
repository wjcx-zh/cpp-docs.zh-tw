---
title: 編譯器限制
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9663da06c97886ef1cd20ca2928944795b39dc18
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222201"
---
# <a name="compiler-limits"></a>編譯器限制

C++ 標準會建議各種語言的建構限制。 以下是一份的情況下，MicrosoftC++編譯器不會實作所建議的限制。 第一個數字是 ISO 中建立的限制C++11 標準 (INCITS/ISO/IEC 14882-2011 [2012]，Annex B) 第二個數字是 Microsoft 實作的限制C++編譯器：

- 巢狀層級的複合陳述式、 反覆項目控制結構，以及選取控制結構-C++標準：256，MicrosoftC++編譯器： 視陳述式的巢狀，但通常介於 100 和 110 之間的組合。

- 一個巨集定義-中的參數C++標準：256，MicrosoftC++編譯器：127.

- 在一個巨集引動過程的引數C++標準：256，MicrosoftC++編譯器： 127。

- 中字元的字元字串常值或寬字串常值 （串連之後）-C++標準：65536，MicrosoftC++編譯器：65535 的單一位元組字元，包括 NULL 結束字元和 32767 雙位元組字元，包括 NULL 結束字元。

- 層級的巢狀的類別、 結構或等位的定義，在單一`struct-declaration-list`-C++標準：256，MicrosoftC++編譯器：16.

- 成員初始設定式中建構函式定義為C++標準：6144，MicrosoftC++編譯器： 至少 6144。

- 範圍限定性條件的識別碼-C++標準：256，MicrosoftC++編譯器：127.

- 巢狀**extern**規格-C++標準：1024，MicrosoftC++編譯器：9 (不計入隱含**extern**規格在全域範圍或 10，如果您計算隱含**extern**規格在全域範圍中的...

- 樣板宣告-中的樣板引數C++標準：1024，MicrosoftC++編譯器：2046.

## <a name="see-also"></a>另請參閱

[非標準行為](../cpp/nonstandard-behavior.md)