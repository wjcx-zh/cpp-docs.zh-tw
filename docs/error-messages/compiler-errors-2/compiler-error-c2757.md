---
title: 編譯器錯誤 C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: 98b43a2f3c0888fc385226cd80889b9911c84690
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668516"
---
# <a name="compiler-error-c2757"></a>編譯器錯誤 C2757

'symbol': 已經有同名的符號，因此無法使用此名稱做為命名空間名稱

因為命名空間識別項已在使用參考的組件中，目前編譯中所使用的符號。

下列範例會產生 C2757:

```
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

然後，

```
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
