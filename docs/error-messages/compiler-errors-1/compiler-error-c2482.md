---
title: 編譯器錯誤 C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564810"
---
# <a name="compiler-error-c2482"></a>編譯器錯誤 C2482

>'*識別碼*': 'thread' 允許的資料不受管理/WinRT 程式碼中的動態初始設定

## <a name="remarks"></a>備註

在 managed 或 WinRT 程式碼的變數宣告可透過[__declspec （thread)](../../cpp/thread.md)儲存類別修飾詞的屬性或[thread_local](../../cpp/storage-classes-cpp.md#thread_local)儲存類別規範 nelze s položkami 運算式需要在執行階段的評估。 靜態運算式，才能初始化`__declspec(thread)`或`thread_local`在這些執行階段環境中的資料。

## <a name="example"></a>範例

下列範例會產生 C2482 中受管理 (**/clr**) 和 WinRT (**/ZW**) 程式碼：

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

若要修正此問題，請使用常數，來初始化執行緒區域儲存區**constexpr**，或靜態的運算式。 個別執行任何執行緒特定的初始化。