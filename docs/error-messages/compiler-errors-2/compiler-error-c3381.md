---
title: 編譯器錯誤 C3381
description: Microsoft c + + 編譯器錯誤 C3381、其原因和解決方式。
ms.date: 09/28/2020
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: 48a6c81f9506c532333b5353b8b194d17c91043f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510145"
---
# <a name="compiler-error-c3381"></a>編譯器錯誤 C3381

> '*identifier*'：元件存取規範只適用于以/clr 選項編譯的程式碼

類型是使用存取規範來宣告或定義的，只有在使用編譯的程式碼中才允許 **`/clr`** 。

## <a name="remarks"></a>備註

這個錯誤可能是因為錯置 **`public`** 、 **`protected`** 或 **`private`** 關鍵字，或遺漏冒號 (在 **`:`** 或中的存取規範之後) **`class`** **`struct`** 。

在 c + +/CLI 中，原生類型可以在元件外部看見，但您只能在編譯中指定原生類型的元件存取 **`/clr`** 。 如需詳細資訊，請參閱[類型可見度](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[ `/clr` (Common Language Runtime 編譯) ](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C3381。 若要修正此問題，請先 **`public`** 從定義中移除規範 `class A` ，或使用選項進行編譯 **`/clr`** 。 接下來，在後面加上冒號 **`private`** 以指定的存取權 `class B {} b;` 。 這是因為嵌套類別在其宣告中不能有元件存取規範。

```cpp
// C3381.cpp
// compile with: /c
public class A {   // C3381
    private class B {} b;   // C3381
};
```
