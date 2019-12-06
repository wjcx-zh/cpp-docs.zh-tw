---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: 6e424846c46dd50852b62008c4f1f38827da849c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857407"
---
# <a name="noinline"></a>noinline

**Microsoft 專屬**

**__declspec （noinline）** 會告知編譯器永遠不會內嵌特定的成員函式（類別中的函式）。

如果函式不大，而且對程式碼的效能不重要，建議不要內嵌函式。 也就是，如果函式不大且可能不常被呼叫，例如處理錯誤條件的函式。

請記住，如果函式標記為**noinline**，呼叫函式將會較小，因此本身是編譯器內嵌的候選項。

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[inline、__inline、\__forceinline](inline-functions-cpp.md)
