---
title: 編譯器警告 （層級 1） C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: dcb7062c751320a9f9c612b42caf6d018047d8d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380834"
---
# <a name="compiler-warning-level-1-c4838"></a>編譯器警告 （層級 1） C4838

從 'type_1' 轉換成 'type_2' 必須是縮小轉換

使用彙總或清單初始化時，找不到隱含的縮小轉換。

C 語言允許隱含的縮小轉換在指派和初始化，並C++符合如下所示，即使未預期的縮小是許多程式碼錯誤的原因。 若要讓程式碼更安全，C++標準要求的診斷訊息，初始化清單中的縮小轉換發生時。 在視覺效果C++，是診斷[編譯器錯誤 C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md)使用統一初始化語法支援從 Visual Studio 2015 開始時。 編譯器會產生警告 C4838 時使用 清單 或 Visual Studio 2013 所支援的彙總初始化語法。

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