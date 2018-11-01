---
title: 編譯器錯誤 C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470586"
---
# <a name="compiler-error-c3813"></a>編譯器錯誤 C3813

屬性宣告只可以出現於 managed 或 WinRT 類型的定義中

A[屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能宣告在 managed 或 Windows 執行階段型別。 原生類型不支援 `property` 關鍵字。

## <a name="example"></a>範例

下列範例會產生 C3813，並說明如何加以修正：

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```