---
title: 編譯器警告 （層級 1） C4838 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1335d9c36f6764b54689a8334a91f11275ee3265
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025447"
---
# <a name="compiler-warning-level-1-c4838"></a>編譯器警告 （層級 1） C4838

從 'type_1' 轉換成 'type_2' 必須是縮小轉換

使用彙總或清單初始化時，找不到隱含的縮小轉換。

C 語言允許隱含的縮小轉換在指派和初始化，以及 c + + 會遵循花色，即使未預期的縮小是許多程式碼錯誤的原因。 若要讓程式碼更安全，c + + 標準需要診斷訊息時縮小轉換，就會發生在初始設定清單中。 Visual c + + 中是診斷[編譯器錯誤 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)使用統一初始化語法支援從 Visual Studio 2015 開始時。 編譯器會產生警告 C4838 時使用 清單 或 Visual Studio 2013 所支援的彙總初始化語法。

當您知道已轉換值的可能範圍可放入目標時，縮小轉換可以是沒問題。 在此情況下，您知道多個與編譯器。 若要刻意縮小轉換，讓您自己的意願明確使用靜態轉型。 否則，這則警告訊息幾乎都表示您的程式碼發生錯誤。 您可以藉由確定您初始化的物件具有夠大，無法處理輸入的類型來修正此問題。

下列範例會產生 C4838，並示範修正此問題的一種方法：

```
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```