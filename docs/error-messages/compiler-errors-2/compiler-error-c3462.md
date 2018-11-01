---
title: 編譯器錯誤 C3462
ms.date: 11/04/2016
f1_keywords:
- C3462
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
ms.openlocfilehash: 6c56e59be8bc4173c6568b47628f675ba4f4d782
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651772"
---
# <a name="compiler-error-c3462"></a>編譯器錯誤 C3462

'type': 只能轉送匯入的類型

TypeForwardedTo 屬性必須套用至參考的中繼資料中的類型。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>範例

下列範例會產生 C3462：

```
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```