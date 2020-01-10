---
title: 編譯器錯誤 C3618
ms.date: 11/04/2016
f1_keywords:
- C3618
helpviewer_keywords:
- C3618
ms.assetid: cacc105d-4389-4cb8-ae6c-41a3622e9a86
ms.openlocfilehash: 6f0edf1addf753054fbc50a1591b5b1a37394087
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759720"
---
# <a name="compiler-error-c3618"></a>編譯器錯誤 C3618

' function '：無法定義標記為 DllImport 的方法

以 <xref:System.Runtime.InteropServices.DllImportAttribute> 標記的方法會在指定的中定義。URLMON.DLL.

## <a name="example"></a>範例

下列範例會產生 C3618。

```cpp
// C3618.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[ DllImport("user32.dll", EntryPoint="MessageBox", CharSet=CharSet::Ansi) ]  // CHANGED
void Func();

void Func() {}   // C3618, remove this function definition to resolve
```
