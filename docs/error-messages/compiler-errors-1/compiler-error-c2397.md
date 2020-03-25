---
title: 編譯器錯誤 C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 02a8bb09e0b22619bd61e6c4675057263a62a9d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206011"
---
# <a name="compiler-error-c2397"></a>編譯器錯誤 C2397

從 ' type_1 ' 轉換為 ' type_2 ' 需要縮小轉換

使用統一初始化時找到隱含的縮小轉換。

C 語言允許在指派和初始化中進行隱含縮小轉換， C++並遵循，即使非預期的縮小是造成許多程式碼錯誤的原因也一樣。 為了讓程式碼更安全C++ ，當初始化清單中發生縮小轉換時，標準需要診斷訊息。 在 Visual C++中，使用從 Visual Studio 2015 開始支援的統一初始化語法時，診斷是編譯器錯誤 C2397。 當使用 Visual Studio 2013 所支援的清單或匯總初始化語法時，編譯器會產生[編譯器警告（層級1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) 。

當您知道可能的轉換值範圍可以放在目標中時，縮小轉換可能會很好。 在這種情況下，您所知的不僅僅是編譯器。 如果您刻意進行縮小轉換，請使用靜態轉換，讓您的意圖明確。 否則，此錯誤訊息幾乎一律會指出您的程式碼中有錯誤。 您可以藉由確定您初始化的物件具有夠大的類型來處理輸入，藉以修正此問題。

下列範例會產生 C2397，並顯示解決此問題的一種方法：

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
