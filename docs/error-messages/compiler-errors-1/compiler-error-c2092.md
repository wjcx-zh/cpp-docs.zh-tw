---
title: 編譯器錯誤 C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: 8f2b83b4099308ea1d0bb127d8cea377ab65da96
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741887"
---
# <a name="compiler-error-c2092"></a>編譯器錯誤 C2092

' 陣列名稱稱 ' 陣列元素類型不可為函數

不允許函數陣列。 使用函式的指標陣列。

## <a name="examples"></a>範例

下列範例會產生 C2092：

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

可能的解決方式：

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
