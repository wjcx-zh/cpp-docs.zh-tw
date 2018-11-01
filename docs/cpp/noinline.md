---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: 3a8dce21aa707a1a52c647c9efee5ab806511ca8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454557"
---
# <a name="noinline"></a>noinline

## <a name="microsoft-specific"></a>Microsoft 特定的

**__declspec （noinline)** 會告知編譯器永遠不要內嵌特定成員函式 （在類別中的函式）。

如果函式不大，而且對程式碼的效能不重要，建議不要內嵌函式。 也就是，如果函式不大且可能不常被呼叫，例如處理錯誤條件的函式。

請記住，如果函式標示**noinline**，呼叫的函式會較小，因此，本身為編譯器的內嵌的候選項目。

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[inline、__inline、\__forceinline](inline-functions-cpp.md)

