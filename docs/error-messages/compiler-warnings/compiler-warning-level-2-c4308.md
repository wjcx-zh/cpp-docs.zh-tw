---
title: 編譯器警告 (層級 2) C4308
ms.date: 11/04/2016
f1_keywords:
- C4308
helpviewer_keywords:
- C4308
ms.assetid: d4e5c53c-71b2-4bbc-8a7c-3a2a3180d9d9
ms.openlocfilehash: f97d66f9e3445d022adc3362532774b15ea09961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402485"
---
# <a name="compiler-warning-level-2-c4308"></a>編譯器警告 (層級 2) C4308

負整數常數轉換成不帶正負號的類型

運算式會將負整數常數轉換成不帶正負號的型別。 運算式的結果是可能沒有意義。

## <a name="example"></a>範例

```
// C4308.cpp
// compile with: /W2
unsigned int u = (-5 + 3U);   // C4308

int main()
{
}
```