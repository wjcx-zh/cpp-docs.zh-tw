---
title: 編譯器錯誤 C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: a68c3f06daf977bda4700a293803859d4aa96771
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216202"
---
# <a name="compiler-error-c2482"></a>編譯器錯誤 C2482

>'*identifier*'： Managed/WinRT 程式碼中不允許 ' thread ' 資料的動態初始化

## <a name="remarks"></a>備註

在 managed 或 WinRT 程式碼中，使用[__declspec （執行緒）](../../cpp/thread.md)儲存類別修飾詞屬性或[thread_local](../../cpp/storage-classes-cpp.md#thread_local)儲存類別規範所宣告的變數，無法使用需要在執行時間進行評估的運算式進行初始化。 必須要有靜態運算式，才能 `__declspec(thread)` **`thread_local`** 在這些執行時間環境中初始化或資料。

## <a name="example"></a>範例

下列範例會產生 managed （**/clr**）和 WinRT （**/ZW**）程式碼中的 C2482：

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

若要修正此問題，請使用常數、或靜態運算式來初始化執行緒區域儲存區 **`constexpr`** 。 分別執行任何執行緒特定的初始化。
