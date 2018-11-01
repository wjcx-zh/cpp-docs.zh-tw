---
title: 編譯器錯誤 C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: 0a1b0b82241c6e48d2c1941ff8122697d11492eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587729"
---
# <a name="compiler-error-c3808"></a>編譯器錯誤 C3808

> '*型別*': 具有 ComImport 屬性的類別不可定義成員'*成員*'、 只抽象或 dllimport 函式允許

## <a name="remarks"></a>備註

衍生自類型<xref:System.Runtime.InteropServices.ComImportAttribute>不能定義*成員*。

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

下列範例會產生 C3808。

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```