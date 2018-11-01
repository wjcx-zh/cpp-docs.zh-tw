---
title: 編譯器警告 （層級 2） C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 73805afc897d14c6d2cc87490dfa0769a8de5193
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488396"
---
# <a name="compiler-warning-level-2-c4094"></a>編譯器警告 （層級 2） C4094

未標記 ' token' 宣告沒有符號

編譯器偵測到使用未標記的結構、 等位或類別的空白宣告。 宣告會被忽略。

## <a name="example"></a>範例

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

這種情況會產生 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。