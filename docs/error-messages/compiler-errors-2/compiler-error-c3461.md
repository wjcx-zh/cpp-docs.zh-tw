---
title: 編譯器錯誤 C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: c5195e0a9bba1bc9e5962f3d3ae1795bb098be3d
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742875"
---
# <a name="compiler-error-c3461"></a>編譯器錯誤 C3461

'type': 只能轉送 Managed 類型

類型轉送只能在 CLR 類型上執行。  如需詳細資訊，請參閱 [類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md) 。

如需詳細資訊，請參閱 [類型轉送 (c + +/cli) ](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="examples"></a>範例

下列範例會建立元件。

```cpp
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

下列範例會產生 C3461。

```cpp
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
