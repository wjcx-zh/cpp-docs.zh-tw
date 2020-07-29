---
title: 編譯器警告 (層級 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: ba2e1e7eb490a28626937a3911608ff9686d6f38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195976"
---
# <a name="compiler-warning-level-4-c4565"></a>編譯器警告 (層級 4) C4565

> '*function*'：重複定義;符號先前已使用 __declspec （*修飾*詞）宣告

## <a name="remarks"></a>備註

符號已重新定義或重新宣告，而第二個定義或宣告與第一個定義或宣告不同，但沒有 **`__declspec`** 修飾詞（*修飾*詞）。 這個警告僅供參考。 若要修正這個警告，請刪除其中一個定義。

## <a name="example"></a>範例

下列範例會產生 C4565：

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
