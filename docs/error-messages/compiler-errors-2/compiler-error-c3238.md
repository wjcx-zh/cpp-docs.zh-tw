---
title: 編譯器錯誤 C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: 1f238a3be27023c755544438166aae1b2b2967d3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741979"
---
# <a name="compiler-error-c3238"></a>編譯器錯誤 C3238

'type': 具有這個名稱的類型已轉送至組件 'assembly'

在用戶端應用程式定義的類型，也透過類型轉送語法定義在參考的組件中。 在應用程式範圍內，無法定義這兩種類型。

如需詳細資訊，請參閱 [ (c + +/cli 的型別轉送) ](../../extensions/type-forwarding-cpp-cli.md) 。

## <a name="examples"></a>範例

下列範例會建立組件，其中所包含的類型是從另一個組件轉送過來。

```cpp
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

下列範例會建立包含類型定義的組件，而不只是包含類型轉送語法。

```cpp
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

下列範例會產生 C3238：

```cpp
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```
