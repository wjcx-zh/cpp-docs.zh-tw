---
title: 編譯器錯誤 C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 889d9a108ab0dfb0101fb9ec9c367db9378b1128
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757133"
---
# <a name="compiler-error-c3809"></a>編譯器錯誤 C3809

'class'：Managed 或 WinRT 類型不可以有任何的 friend 函式/類別/介面

Managed 類型和 Windows 執行階段類型不允許 friends。 若要修正這個錯誤，請不要在 Managed 或 Windows 執行階段類型中宣告 friends。

下列範例會產生 C3809：

```cpp
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```
