---
title: 編譯器錯誤 C3466
ms.date: 11/04/2016
f1_keywords:
- C3466
helpviewer_keywords:
- C3466
ms.assetid: 69a877d9-a749-474b-bfc3-8d3fd53ba8fd
ms.openlocfilehash: 6eae1c44d8dae9118258c83c5919947803f49215
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777246"
---
# <a name="compiler-error-c3466"></a>編譯器錯誤 C3466

'type': 泛型類別的特製化無法轉送

您無法使用類型轉送泛型類別的特製化上。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md)。</c0>

## <a name="example"></a>範例

下列範例會建立元件。

```
// C3466.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>範例

下列範例會產生 C3466。

```
// C3466_b.cpp
// compile with: /clr /c
#using "C3466.dll"
[assembly:TypeForwardedTo(GR<int>::typeid)];   // C3466
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```