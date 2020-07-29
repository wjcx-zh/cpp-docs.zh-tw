---
title: 編譯器警告 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: baf74733c94fdb03f130d2300d0918845cc4de4c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223326"
---
# <a name="compiler-warning-c4439"></a>編譯器警告 C4439

' function '：簽章中具有 managed 類型的函式定義必須有 __clrcall 呼叫慣例

編譯器會以隱含方式取代呼叫慣例 [`__clrcall`](../../cpp/clrcall.md) 。 若要解決這個警告，請移除 **`__cdecl`** 或 **`__stdcall`** 呼叫慣例。

C4439 一律會發出為錯誤。 您可以使用或來關閉此警告 `#pragma warning` **`/wd`** ; 如需詳細資訊，請參閱[warning](../../preprocessor/warning.md)或[/w、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/wo、/Wv、/wx （警告層級）](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>範例

下列範例會產生 C4439。

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
