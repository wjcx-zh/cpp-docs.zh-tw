---
title: 編譯器錯誤 C3460
ms.date: 11/04/2016
f1_keywords:
- C3460
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
ms.openlocfilehash: 9ffbc5102855574aba668a2c501cd08dbaebe5b8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775175"
---
# <a name="compiler-error-c3460"></a>編譯器錯誤 C3460

'type': 只能轉送使用者定義的類型

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../extensions/type-forwarding-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3460.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>範例

下列範例會產生 C3460。

```
// C3460_b.cpp
// compile with: /clr /c
#using "C3460.dll"
[assembly:TypeForwardedTo(int::typeid)];   // C3460
[assembly:TypeForwardedTo(R::typeid)];
```