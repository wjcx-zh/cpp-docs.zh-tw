---
title: 編譯器錯誤 C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: 185bd35bb732f592c75912fe69d4491252fe9d0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476111"
---
# <a name="compiler-error-c3468"></a>編譯器錯誤 C3468

'type': 您只可以將類型轉送到組件:

'`file`' 不是組件

僅能轉送組件中的類型。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會建立模組。

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>範例

下列範例會產生 C3468。

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```