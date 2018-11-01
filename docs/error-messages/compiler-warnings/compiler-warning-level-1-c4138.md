---
title: 編譯器警告 (層級 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: 96f8915b9bec166496ca4305d796ce8ef514ca15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481675"
---
# <a name="compiler-warning-level-1-c4138"></a>編譯器警告 (層級 1) C4138

在註解外部找到 '*/'

結案註解分隔符號必須在開啟註解分隔符號之後。 編譯器會假設星號 (<strong>\*</strong>) 和正斜線 (/) 之間有個空格。

## <a name="example"></a>範例

```
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

此警告可能因嘗試巢狀化註解所致。

如果您將包含註解的程式碼區段註解化，再將程式碼括在 **#if / #endif** 區塊中，並將控制運算式設定為零，應可解決此警告：

```
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```