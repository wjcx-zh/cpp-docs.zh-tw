---
title: 編譯器警告 (層級 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 03ce38aaa910a410025c5cccdf39646d34104779
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052381"
---
# <a name="compiler-warning-level-1-c4788"></a>編譯器警告 (層級 1) C4788

' identifier '：識別碼已截斷為 ' number ' 個字元

編譯器會限制函數名稱允許的長度上限。 當編譯器產生 EH/SEH 程式碼的 funclets 時，它會藉由在函式名稱前面加上一些文字來形成 funclet 名稱，例如 "__catch"、"\__unwind" 或另一個字串。

產生的 funclet 名稱可能太長，編譯器會將它截斷並產生 C4788。

若要解決這個警告，請縮短原始函數名稱。 如果函式是C++樣板函式或方法，請對名稱的一部分使用 typedef。 例如:

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

可以取代成：

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

這個警告只會發生在 x64 編譯器中。