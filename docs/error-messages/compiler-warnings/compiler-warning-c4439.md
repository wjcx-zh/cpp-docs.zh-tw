---
title: 編譯器警告 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 7cab2e55fca640438051fbb79ac933e83d5f3cbb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623660"
---
# <a name="compiler-warning-c4439"></a>編譯器警告 C4439

' function '：簽章中具有 managed 類型的函式定義必須有 __clrcall 呼叫慣例

編譯器會隱含地以[__clrcall](../../cpp/clrcall.md)取代呼叫慣例。 若要解決這個警告，請移除 `__cdecl` 或 `__stdcall` 呼叫慣例。

C4439 一律會發出為錯誤。 您可以使用 `#pragma warning` 或 **/wd**關閉此警告;如需詳細資訊，請參閱[warning](../../preprocessor/warning.md)或[/w、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/wo、/Wv、/Wx （警告層級）](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>範例

下列範例會產生 C4439。

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```