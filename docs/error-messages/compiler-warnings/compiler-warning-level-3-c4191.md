---
title: 編譯器警告 (層級 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: cd0d7dc57c8d3c94a52f72b536657bb3ea1c6b3a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051873"
---
# <a name="compiler-warning-level-3-c4191"></a>編譯器警告 (層級 3) C4191

'operator/operation': 從 'type of expression' 到 'type required' 不安全的轉換

與函式指標有關的數項作業被視為不安全：

- 具有不同呼叫慣例的函式類型。

- 具有不同傳回慣例的函式類型。

- 具有不同大小、類型分類或分類的引數或傳回類型。

- 區隔引數清單的長度 (在 `__cdecl`，只有從較長的清單轉換成較短的清單，即使較短的是 varargs)。

- 對函式的指標進行別名的資料指標（不是**void** <strong>\*</strong>）。

- 會在 `reinterpret_cast`產生錯誤或警告的任何其他類型差異。

透過結果指標呼叫這個函式可能會導致程式當機。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

下列範例會產生 C4191：

```cpp
// C4191.cpp
// compile with: /W3 /clr
#pragma warning(default: 4191)

void __clrcall f1() { }
void __cdecl   f2() { }

typedef void (__clrcall * fnptr1)();
typedef void (__cdecl   * fnptr2)();

int main() {
   fnptr1 fp1 = static_cast<fnptr1>(&f1);
   fnptr2 fp2 = (fnptr2) &f2;

   fnptr1 fp3 = (fnptr1) &f2;   // C4191
   fnptr2 fp4 = (fnptr2) &f1;   // C4191
};
```