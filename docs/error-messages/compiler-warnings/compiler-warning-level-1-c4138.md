---
title: 編譯器警告 (層級 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e1f28f5afb1879229ff0d408cb576312966e1c81
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200105"
---
# <a name="compiler-warning-level-1-c4138"></a>編譯器警告 (層級 1) C4138

在註解外部找到 '*/'

結案註解分隔符號必須在開啟註解分隔符號之後。 編譯器會假設星號 (<strong>\*</strong>) 和正斜線 (/) 之間有個空格。

## <a name="example"></a>範例

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

此警告可能因嘗試巢狀化註解所致。

如果您將包含註解的程式碼區段註解化，再將程式碼括在 **#if / #endif** 區塊中，並將控制運算式設定為零，應可解決此警告：

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```
