---
title: 編譯器錯誤 C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 88aca16363af22a6671832264889b1a26e43d460
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223365"
---
# <a name="compiler-error-c3813"></a>編譯器錯誤 C3813

屬性宣告只可以出現於 managed 或 WinRT 類型的定義中

[屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能在 managed 或 Windows 執行階段類型中宣告。 原生類型不支援 **`property`** 關鍵字。

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
