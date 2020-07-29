---
title: 編譯器警告 (層級 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 66e782c2fbb9c39c6a189de496cd0dcb4f1f4991
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218074"
---
# <a name="compiler-warning-level-4-c4559"></a>編譯器警告 (層級 4) C4559

> '*function*'：重複定義;函數增益 __declspec （*修飾*詞）

## <a name="remarks"></a>備註

已重新定義或重新宣告函式，而第二個定義或宣告已加入 **`__declspec`** 修飾詞（*修飾*詞）。 這個警告僅供參考。 若要修正這個警告，請刪除其中一個定義。

## <a name="example"></a>範例

下列範例會產生 C4559：

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
