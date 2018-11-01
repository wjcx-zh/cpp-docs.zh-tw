---
title: 編譯器錯誤 C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: 81372c7a2468becf6dba3b30b62ee266eed272ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562912"
---
# <a name="compiler-error-c3461"></a>編譯器錯誤 C3461

'type': 只能轉送 Managed 類型

類型轉送只能在 CLR 類型上執行。  請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)如需詳細資訊。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>範例

下列範例會產生 C3461。

```
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```