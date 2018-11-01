---
title: 編譯器錯誤 C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 5f39510ee9ec0e717d675aa8b396405bc33b4ea1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445002"
---
# <a name="compiler-error-c3279"></a>編譯器錯誤 C3279

cli 命名空間中宣告的類別樣板，不允許部分和明確特製化以及明確具現化

`cli` 命名空間由 Microsoft 所定義，並包含虛擬範本。 在這個命名空間中，Visual C++ 編譯器不允許使用者定義的部分和明確特製化，以及類別樣板的明確具現化。

下列範例會產生 C3279：

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```