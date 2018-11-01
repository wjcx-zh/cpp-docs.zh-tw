---
title: 編譯器警告 (層級 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: c51a4409c2a3028823462539343654b5eac365d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598168"
---
# <a name="compiler-warning-level-1-c4788"></a>編譯器警告 (層級 1) C4788

'identifier': 識別項被截斷成 'number' 個字元

編譯器限制的函式名稱所允許的最大長度。 當編譯器產生 funclets EH/SEH 的程式碼時，它會構成 funclet 名稱前面加上一些文字的函式名稱，例如 「 __catch"，"\__unwind"，或另一個字串。

產生的 funclet 名稱可能太長，而且編譯器將會截斷，並產生 C4788。

若要解決這個警告，請縮短原始函式名稱。 如果函式是 c + + 範本函式或方法，使用 typedef 名稱的組件。 例如: 

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

可以藉由取代：

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

這個警告只發生在 x64 編譯器。