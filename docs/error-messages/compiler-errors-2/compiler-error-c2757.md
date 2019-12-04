---
title: 編譯器錯誤 C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: a9f4661495e0fa5219a517b6f6ca410323a77269
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759525"
---
# <a name="compiler-error-c2757"></a>編譯器錯誤 C2757

' symbol '：具有這個名稱的符號已經存在，因此這個名稱不能用來做為命名空間名稱

目前編譯中用來當做命名空間識別碼的符號已經用於參考的元件中。

下列範例會產生 C2757：

```cpp
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

然後，

```cpp
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
