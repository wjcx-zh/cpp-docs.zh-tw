---
title: 編譯器錯誤 C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749564"
---
# <a name="compiler-error-c3381"></a>編譯器錯誤 C3381

' assembly '：元件存取規範僅適用于以/clr 選項編譯的程式碼

可以在元件外部看到原生類型，但您只能在 **/clr**編譯中指定原生類型的元件存取。

如需詳細資訊，請參閱[類型可見度](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[/Clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C3381。

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
