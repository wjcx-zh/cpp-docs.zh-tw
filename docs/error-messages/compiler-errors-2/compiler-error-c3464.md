---
title: 編譯器錯誤 C3464
ms.date: 11/04/2016
f1_keywords:
- C3464
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
ms.openlocfilehash: ddfd795465af559885ad05775d87d6188f2f13a8
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742849"
---
# <a name="compiler-error-c3464"></a>編譯器錯誤 C3464

'type' 巢狀類型不可轉送

類型轉送未作用於巢狀類型上。

如需詳細資訊，請參閱 [類型轉送 (c + +/cli) ](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="examples"></a>範例

下列範例會建立元件。

```cpp
// C3464.cpp
// compile with: /LD /clr
public ref class R {
public:
   ref class N {};
};
```

下列範例會產生 C3464。

```cpp
// C3464_b.cpp
// compile with: /clr /c
#using "C3464.dll"
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
