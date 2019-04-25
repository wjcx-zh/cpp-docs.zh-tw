---
title: 編譯器錯誤 C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: 70375950543b9525fca10fff3084c923095fa35e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173479"
---
# <a name="compiler-error-c3467"></a>編譯器錯誤 C3467

'type': 這個類型已經轉送了

編譯器發現相同類型的多個轉送類型宣告。 每種類型只允許一個宣告。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md)。</c0>

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>範例

下列範例會產生 C3467。

```
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```