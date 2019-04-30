---
title: 編譯器錯誤 C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 61f23269e0b6ed65a485f11e49e492d2248b8a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378930"
---
# <a name="compiler-error-c2397"></a>編譯器錯誤 C2397

從 'type_1' 轉換成 'type_2' 必須是縮小轉換

使用統一初始設定時，找不到隱含的縮小轉換。

C 語言允許隱含的縮小轉換在指派和初始化，並C++符合如下所示，即使未預期的縮小是許多程式碼錯誤的原因。 若要讓程式碼更安全，C++標準要求的診斷訊息，初始化清單中的縮小轉換發生時。 在視覺效果C++，使用一致的初始化語法支援從 Visual Studio 2015 時，診斷是編譯器錯誤 C2397。 編譯器會產生[編譯器警告 （層級 1） C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md)時使用 [清單] 或 [Visual Studio 2013] 所支援的彙總初始化語法。

當您知道已轉換值的可能範圍可放入目標時，縮小轉換可以是沒問題。 在此情況下，您知道多個與編譯器。 若要刻意縮小轉換，讓您自己的意願明確使用靜態轉型。 否則，此錯誤訊息幾乎都表示程式碼中有 bug。 您可以藉由確定您初始化的物件具有夠大，無法處理輸入的類型來修正此問題。

下列範例會產生 C2397，並示範修正此問題的一種方法：

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