---
title: 編譯器錯誤 C3469 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3469
dev_langs:
- C++
helpviewer_keywords:
- C3469
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39889052b85ee6ab5595f388f939403fe3d2a46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016984"
---
# <a name="compiler-error-c3469"></a>編譯器錯誤 C3469

'type': 泛型類別無法轉送

您無法對泛型類別使用類型轉送。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3469.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>範例

下列範例會產生 C3466。

```
// C3469_b.cpp
// compile with: /clr /c
#using "C3469.dll"
[assembly:TypeForwardedTo(GR::typeid)];   // C3469
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```