---
title: 編譯器錯誤 C3462
ms.date: 11/04/2016
f1_keywords:
- C3462
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
ms.openlocfilehash: f267d195ba851a9d585961848062fa271168aeb8
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743330"
---
# <a name="compiler-error-c3462"></a>編譯器錯誤 C3462

'type': 只能轉送匯入的類型

TypeForwardedTo 屬性必須套用至參考的中繼資料中的類型。

如需詳細資訊，請參閱 [類型轉送 (c + +/cli) ](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="examples"></a>範例

下列範例會建立元件。

```cpp
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

下列範例會產生 C3462：

```cpp
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```
