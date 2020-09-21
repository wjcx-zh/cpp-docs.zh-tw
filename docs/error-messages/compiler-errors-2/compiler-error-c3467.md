---
title: 編譯器錯誤 C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: dd7046fcf87a6b8f095092ef0de4b94326151e87
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742823"
---
# <a name="compiler-error-c3467"></a>編譯器錯誤 C3467

'type': 這個類型已經轉送了

編譯器發現相同類型的多個轉送類型宣告。 每種類型只允許一個宣告。

如需詳細資訊，請參閱 [類型轉送 (c + +/cli) ](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="examples"></a>範例

下列範例會建立元件。

```cpp
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

下列範例會產生 C3467。

```cpp
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```
