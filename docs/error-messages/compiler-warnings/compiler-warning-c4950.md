---
title: 編譯器警告 C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 52c4de94dfe087b4dcf407295e556c9350b2cb8b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164985"
---
# <a name="compiler-warning-c4950"></a>編譯器警告 C4950

'type_or_member' : 標記為過時

成員或類型已使用 <xref:System.ObsoleteAttribute> 屬性標示為已淘汰。

C4950 一律發出為錯誤。 您可以使用[warning](../../preprocessor/warning.md) pragma 指示詞或[/wd](../../build/reference/compiler-option-warning-level.md)編譯器選項來關閉此警告。

## <a name="example"></a>範例

下列範例會產生 C4950：

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```
